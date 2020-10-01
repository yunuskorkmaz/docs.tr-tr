---
title: Visual Studio 'da AJAX etkin bir WCF hizmeti ve ASP.NET Istemcisi oluşturma
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 0bfe55c68f68bfef7b7ec2034413b53d41b0c785
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609362"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma

Bu konuda, Visual Studio kullanarak hizmete erişen bir AJAX özellikli Windows Communication Foundation (WCF) hizmeti ve bir ASP.NET istemcisi oluşturma konusu gösterilmektedir.

## <a name="create-an-aspnet-web-app"></a>ASP.NET web uygulaması oluşturma

1. Visual Studio'yu açın.

1. **Dosya** menüsünden **Yeni**  >  **Proje** ' yi seçin.

1. **Yeni proje** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Web** kategorisini genişletin ve sonra **ASP.NET Web uygulaması (.NET Framework)** öğesini seçin.

1. Projeyi **SandwichServices** olarak adlandırın ve **Tamam**' a tıklayın.

1. **Yeni ASP.NET Web uygulaması** Iletişim kutusunda **boş** ' ı seçin ve ardından **Tamam**' ı seçin.

   ![Visual Studio 'da ASP.NET Web uygulaması türü iletişim kutusu](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a>Web formu ekleme

1. **Çözüm Gezgini** ' de SandwichServices projesine sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Web** kategorisini genişletin ve ardından **Web formu** şablonunu seçin.

1. Varsayılan adı (**WebForm1**) kabul edin ve **Ekle**' yi seçin.

   **Kaynak** görünümünde *WebForm1. aspx* açılır.

1. Aşağıdaki biçimlendirmeyi etiketleri içine ekleyin **\<body>** :

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a>AJAX etkin bir WCF hizmeti oluşturma

1. **Çözüm Gezgini** ' de SandwichServices projesine sağ tıklayın ve **Add**  >  **Yeni öğe**Ekle ' yi seçin.

1. **Yeni öğe Ekle** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Web** kategorisini genişletin ve ardından **WCF hizmeti (AJAX etkin)** şablonunu seçin.

   ![Visual Studio 'da WCF hizmeti (AJAX etkin) öğe şablonu](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. Service **CostService hizmetini** adlandırın ve **Ekle**' yi seçin.

   *CostService.svc.cs* , düzenleyicide açılır.

1. İşlemi hizmette uygulayın. Aşağıdaki yöntemi CostService sınıfına ekleyerek bir Sandwiches miktarının maliyetini hesaplayın:

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a>İstemciyi hizmete erişmek için yapılandırma

1. *WebForm1. aspx* dosyasını açın ve **Tasarım** görünümünü seçin.

2. **Görünüm** menüsünden **araç kutusu**' nu seçin.

3. **AJAX Uzantıları** düğümünü genişletin ve bir **ScriptManager** 'ı sürükleyip form üzerine bırakın.

4. **Kaynak** görünümüne geri döndüğünüzde, **\<ScriptManager>** WCF hizmetinin yolunu belirtmek için Etiketler arasına aşağıdaki kodu ekleyin:

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. JavaScript işlevi için kodu ekleyin `Calculate()` . Web formunun **baş** bölümüne aşağıdaki kodu yerleştirin:

    ```html
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

   Bu kod, üç Sandwiches için fiyat hesaplamak üzere CostService yöntemini çağırır ve sonra sonucu **Additionresult**adlı yayılma alanında görüntüler.

## <a name="run-the-program"></a>Programı çalıştırma

*WebForm1. aspx* ' in odağa sahip olduğundan emin olun ve sonra Web istemcisini başlatmak için **Başlat** düğmesine basın. Düğmenin yeşil bir üçgeni vardır ve **IIS Express (Microsoft Edge)** gibi bir şey diyor. İsterseniz <kbd>F5</kbd>'e de basabilirsiniz. Beklenen "3,75" çıktısını oluşturmak için **3 Sandwiches** düğmesine tıklayın.

## <a name="example"></a>Örnek

*CostService.svc.cs* dosyasındaki tam kod aşağıda verilmiştir:

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

*WebForm1. aspx* sayfasının tüm içerikleri aşağıda verilmiştir:

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
