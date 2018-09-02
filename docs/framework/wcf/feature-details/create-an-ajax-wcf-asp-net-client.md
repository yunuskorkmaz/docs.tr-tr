---
title: Visual Studio'da AJAX etkin bir WCF hizmeti ve bir ASP.NET istemcisi oluşturma
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 07a1e903991e09243572f2a99c19edae7f9793b6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384292"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma

Bu konuda bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmeti ve hizmete erişen bir ASP.NET istemcisi oluşturmak için Visual Studio kullanmayı gösterir.

## <a name="create-an-aspnet-web-app"></a>ASP.NET web uygulaması oluşturma

1. Visual Studio'yu açın.

1. Gelen **dosya** menüsünde **yeni** > **proje**

1. İçinde **yeni proje** iletişim kutusunda Genişlet **yüklü** > **Visual C#** > **Web** kategorisi ve ardından seçin **ASP.NET Web uygulaması (.NET Framework)**.

1. Projeyi adlandırın **SandwichServices** tıklatıp **Tamam**.

1. İçinde **yeni ASP.NET Web uygulaması** iletişim kutusunda **boş** seçip **Tamam**.

   ![Visual Studio'da ASP.NET web uygulaması türü iletişim kutusu](../media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Bir web formu ekleyin

1. SandwichServices projeye sağ **Çözüm Gezgini** seçip **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda Genişlet **yüklü** > **Visual C#** > **Web** kategorisi ve ardından seçin **Web formu** şablonu.

1. Varsayılan adı kabul edin (**WebForm1**) ve ardından **Ekle**.

   *WebForm1.aspx* açılır **kaynak** görünümü.

1. İçinde aşağıdaki işaretlemeyi ekleyin  **\<gövdesi >** etiketler:

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>AJAX etkin bir WCF hizmeti oluşturma

1. SandwichServices projeye sağ **Çözüm Gezgini** seçip **Ekle** > **yeni öğe**.

1. İçinde **Yeni Öğe Ekle** iletişim kutusunda Genişlet **yüklü** > **Visual C#** > **Web** kategorisi ve ardından seçin **WCF Hizmeti (AJAX etkin)** şablonu.

   ![Visual Studio'da WCF Hizmeti (AJAX etkin) öğe şablonu](../media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Hizmet adı **CostService** seçip **Ekle**.

   *CostService.svc.cs* düzenleyicisinde açılır.

1. İşlem hizmette uygulayın. Sandwiches miktarı maliyetini hesaplamak için CostService sınıfına aşağıdaki yöntemi ekleyin:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>Hizmete erişmek için istemciyi Yapılandırma

1. Açık *WebForm1.aspx* seçin ve dosya **tasarım** görünümü.

2. Gelen **görünümü** menüsünde **araç kutusu**.

3. Genişletin **AJAX uzantıları** düğüm ve sürükle ve bırak bir **ScriptManager** forma.

4. Geri **kaynak** görüntülemek için arasına aşağıdaki kodu ekleyin  **\<ScriptManager >** WCF Hizmeti yolunu belirtmek için etiketler:

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. Javascript işlevi için kod ekleme `Calculate()`. Aşağıdaki kodda yerleştirin **baş** web formu bölümünü:

    ```javascript
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
    ```

   Bu kod üç sandwiches fiyatı hesaplamak için CostService yöntemini çağırır ve sonucu adı verilen yayılımda görüntüler **additionResult**.

## <a name="run-the-program"></a>Programı çalıştırın

Emin olun *WebForm1.aspx* odaklı ve tuşuna **Başlat** web istemcisi için düğme. Düğme yeşil üçgenle sahip ve aşağıdaki gibi diyor. **IIS Express (Microsoft Edge)**. Ya da basabilirsiniz **F5**. Tıklayın **3 sandwiches fiyatı** beklenen çıktıyı "3,75" oluşturmak için düğme.

## <a name="example-code"></a>Örnek kod

Tam kod aşağıdadır *CostService.svc.cs* dosyası:

```csharp
using System.ServiceModel;
using System.ServiceModel.Activation;

namespace SandwichServices
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class CostService
    {
        [OperationContract]
        public double CostOfSandwiches(int quantity)
        {
            return 1.25 * quantity;
        }
    }
}
```

Aşağıdadır tam içeriğini *WebForm1.aspx* sayfası:

```aspx-csharp
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="WebForm1.aspx.cs" Inherits="SandwichServices.WebForm1" %>

<!DOCTYPE html>

<html xmlns="http://www.w3.org/1999/xhtml">
<head runat="server">
    <title></title>
    <script type="text/javascript">

        function Calculate() {
            CostService.CostOfSandwiches(3, onSuccess);
        }

        function onSuccess(result) {
            var myres = $get("additionResult");
            myres.innerHTML = result;
        }

    </script>
</head>
<body>
    <form id="form1" runat="server">
        <div>
        </div>
        <asp:ScriptManager ID="ScriptManager1" runat="server">
            <Services>
                <asp:ServiceReference Path="~/CostService.svc" />
            </Services>
        </asp:ScriptManager>

        <input type="button" value="Price of 3 sandwiches" onclick="Calculate()" />
        <br />
        <span id="additionResult"></span>
    </form>
</body>
</html>
```
