import net.runelite.api.Client;
import net.runelite.api.widgets.Widget;
import net.runelite.api.widgets.WidgetInfo;
import net.runelite.client.eventbus.Subscribe;
import net.runelite.client.ui.overlay.Overlay;
import net.runelite.client.ui.overlay.OverlayPanel;
import net.runelite.api.events.GameTick;

import javax.inject.Inject;

public class ShopItemTrackerPlugin extends Overlay
{
    private final Client client;

    @Inject
    public ShopItemTrackerPlugin(Client client)
    {
        this.client = client;
    }

    @Subscribe
    public void onGameTick(GameTick event)
    {
        Widget shopWidget = client.getWidget(WidgetInfo.SHOP_ITEM_CONTAINER);
        if (shopWidget != null)
        {
            // Merr të gjithë artikujt në dyqan dhe shfaq informacione për secilin.
            for (Widget itemWidget : shopWidget.getChildren())
            {
                String itemName = itemWidget.getText(); // Emri i artikujt
                int itemPrice = itemWidget.getItemQuantity(); // Çmimi i artikujt
                
                // Bëj diçka me këto të dhëna (p.sh., shfaqje në një overlay, ruajtje etj.)
                System.out.println("Artikulli: " + itemName + ", Çmimi: " + itemPrice);
            }
        }
    }

    @Override
    public Dimension render(Graphics2D graphics)
    {
        // Mund të shtosh logjikë të vizualizimit këtu, nëse dëshiron të shfaqësh të dhënat
        return null;
    }
}
