---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: AJAX-Enabled WCF hizmeti oluşturma ve hizmete erişen bir ASP.NET Istemcisi'
title: Visual Studio 'da AJAX-Enabled WCF hizmeti ve ASP.NET Istemcisi oluşturma
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 59b0cab9b28dd68b27529b5d880138cc283144a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780355"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="e7da1-103">Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7da1-103">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="e7da1-104">Bu konuda, Visual Studio kullanarak hizmete erişen bir AJAX özellikli Windows Communication Foundation (WCF) hizmeti ve bir ASP.NET istemcisi oluşturma konusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e7da1-104">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="e7da1-105">ASP.NET web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7da1-105">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="e7da1-106">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="e7da1-106">Open Visual Studio.</span></span>

1. <span data-ttu-id="e7da1-107">**Dosya** menüsünden **Yeni**  >  **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-107">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="e7da1-108">**Yeni proje** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Web** kategorisini genişletin ve sonra **ASP.NET Web uygulaması (.NET Framework)** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-108">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="e7da1-109">Projeyi **SandwichServices** olarak adlandırın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e7da1-109">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="e7da1-110">**Yeni ASP.NET Web uygulaması** Iletişim kutusunda **boş** ' ı seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-110">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Visual Studio 'da ASP.NET Web uygulaması türü iletişim kutusu](./media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="e7da1-112">Web formu ekleme</span><span class="sxs-lookup"><span data-stu-id="e7da1-112">Add a web form</span></span>

1. <span data-ttu-id="e7da1-113">**Çözüm Gezgini** ' de SandwichServices projesine sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-113">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="e7da1-114">**Yeni öğe Ekle** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Web** kategorisini genişletin ve ardından **Web formu** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-114">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="e7da1-115">Varsayılan adı (**WebForm1**) kabul edin ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-115">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="e7da1-116">**Kaynak** görünümünde *WebForm1. aspx* açılır.</span><span class="sxs-lookup"><span data-stu-id="e7da1-116">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="e7da1-117">Aşağıdaki biçimlendirmeyi etiketleri içine ekleyin **\<body>** :</span><span class="sxs-lookup"><span data-stu-id="e7da1-117">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="e7da1-118">AJAX etkin bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="e7da1-118">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="e7da1-119">**Çözüm Gezgini** ' de SandwichServices projesine sağ tıklayın ve   >  **Yeni öğe** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-119">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="e7da1-120">**Yeni öğe Ekle** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Web** kategorisini genişletin ve ardından **WCF hizmeti (AJAX etkin)** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-120">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Visual Studio 'da WCF hizmeti (AJAX etkin) öğe şablonu](./media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="e7da1-122">Service **CostService hizmetini** adlandırın ve **Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-122">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="e7da1-123">*CostService.svc.cs* , düzenleyicide açılır.</span><span class="sxs-lookup"><span data-stu-id="e7da1-123">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="e7da1-124">İşlemi hizmette uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e7da1-124">Implement the operation in the service.</span></span> <span data-ttu-id="e7da1-125">Aşağıdaki yöntemi CostService sınıfına ekleyerek bir Sandwiches miktarının maliyetini hesaplayın:</span><span class="sxs-lookup"><span data-stu-id="e7da1-125">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="e7da1-126">İstemciyi hizmete erişmek için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7da1-126">Configure the client to access the service</span></span>

1. <span data-ttu-id="e7da1-127">*WebForm1. aspx* dosyasını açın ve **Tasarım** görünümünü seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-127">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="e7da1-128">**Görünüm** menüsünden **araç kutusu**' nu seçin.</span><span class="sxs-lookup"><span data-stu-id="e7da1-128">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="e7da1-129">**AJAX Uzantıları** düğümünü genişletin ve bir **ScriptManager** 'ı sürükleyip form üzerine bırakın.</span><span class="sxs-lookup"><span data-stu-id="e7da1-129">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="e7da1-130">**Kaynak** görünümüne geri döndüğünüzde, **\<ScriptManager>** WCF hizmetinin yolunu belirtmek için Etiketler arasına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e7da1-130">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```xml
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

5. <span data-ttu-id="e7da1-131">JavaScript işlevi için kodu ekleyin `Calculate()` .</span><span class="sxs-lookup"><span data-stu-id="e7da1-131">Add the code for the JavaScript function `Calculate()`.</span></span> <span data-ttu-id="e7da1-132">Web formunun **baş** bölümüne aşağıdaki kodu yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="e7da1-132">Place the following code in the **head** section of the web form:</span></span>

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

   <span data-ttu-id="e7da1-133">Bu kod, üç Sandwiches için fiyat hesaplamak üzere CostService yöntemini çağırır ve sonra sonucu **Additionresult** adlı yayılma alanında görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e7da1-133">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="e7da1-134">Programı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e7da1-134">Run the program</span></span>

<span data-ttu-id="e7da1-135">*WebForm1. aspx* ' in odağa sahip olduğundan emin olun ve sonra Web istemcisini başlatmak için **Başlat** düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="e7da1-135">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="e7da1-136">Düğmenin yeşil bir üçgeni vardır ve **IIS Express (Microsoft Edge)** gibi bir şey diyor.</span><span class="sxs-lookup"><span data-stu-id="e7da1-136">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="e7da1-137">İsterseniz <kbd>F5</kbd>'e de basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7da1-137">Or, you can press <kbd>F5</kbd>.</span></span> <span data-ttu-id="e7da1-138">Beklenen "3,75" çıktısını oluşturmak için **3 Sandwiches** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e7da1-138">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example"></a><span data-ttu-id="e7da1-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7da1-139">Example</span></span>

<span data-ttu-id="e7da1-140">*CostService.svc.cs* dosyasındaki tam kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e7da1-140">The following is the full code in the *CostService.svc.cs* file:</span></span>

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

<span data-ttu-id="e7da1-141">*WebForm1. aspx* sayfasının tüm içerikleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e7da1-141">The following is the full contents of the *WebForm1.aspx* page:</span></span>

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
