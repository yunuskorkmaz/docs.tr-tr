---
title: Visual Studio'da AJAX etkin bir WCF hizmeti ve bir ASP.NET istemcisi oluşturma
ms.date: 08/17/2018
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 954ee0409f370c3fa28814a70d51334fd75f7b79
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46528846"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="eaab8-102">Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="eaab8-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>

<span data-ttu-id="eaab8-103">Bu konuda bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmeti ve hizmete erişen bir ASP.NET istemcisi oluşturmak için Visual Studio kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaab8-103">This topic shows how to use Visual Studio to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span>

## <a name="create-an-aspnet-web-app"></a><span data-ttu-id="eaab8-104">ASP.NET web uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="eaab8-104">Create an ASP.NET web app</span></span>

1. <span data-ttu-id="eaab8-105">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="eaab8-105">Open Visual Studio.</span></span>

1. <span data-ttu-id="eaab8-106">Gelen **dosya** menüsünde **yeni** > **proje**</span><span class="sxs-lookup"><span data-stu-id="eaab8-106">From the **File** menu, select **New** > **Project**</span></span>

1. <span data-ttu-id="eaab8-107">İçinde **yeni proje** iletişim kutusunda Genişlet **yüklü** > **Visual C#** > **Web** kategorisi ve ardından seçin **ASP.NET Web uygulaması (.NET Framework)**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-107">In the **New Project** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select **ASP.NET Web Application (.NET Framework)**.</span></span>

1. <span data-ttu-id="eaab8-108">Projeyi adlandırın **SandwichServices** tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-108">Name the Project **SandwichServices** and click **OK**.</span></span>

1. <span data-ttu-id="eaab8-109">İçinde **yeni ASP.NET Web uygulaması** iletişim kutusunda **boş** seçip **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-109">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

   ![Visual Studio'da ASP.NET web uygulaması türü iletişim kutusu](media/create-an-ajax-wcf-asp-net-client/new-asp-net-web-app-type.png)

## <a name="add-a-web-form"></a><span data-ttu-id="eaab8-111">Bir web formu ekleyin</span><span class="sxs-lookup"><span data-stu-id="eaab8-111">Add a web form</span></span>

1. <span data-ttu-id="eaab8-112">SandwichServices projeye sağ **Çözüm Gezgini** seçip **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-112">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="eaab8-113">İçinde **Yeni Öğe Ekle** iletişim kutusunda Genişlet **yüklü** > **Visual C#** > **Web** kategorisi ve ardından seçin **Web formu** şablonu.</span><span class="sxs-lookup"><span data-stu-id="eaab8-113">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **Web Form** template.</span></span>

1. <span data-ttu-id="eaab8-114">Varsayılan adı kabul edin (**WebForm1**) ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-114">Accept the default name (**WebForm1**), and then select **Add**.</span></span>

   <span data-ttu-id="eaab8-115">*WebForm1.aspx* açılır **kaynak** görünümü.</span><span class="sxs-lookup"><span data-stu-id="eaab8-115">*WebForm1.aspx* opens in **Source** view.</span></span>

1. <span data-ttu-id="eaab8-116">İçinde aşağıdaki işaretlemeyi ekleyin  **\<gövdesi >** etiketler:</span><span class="sxs-lookup"><span data-stu-id="eaab8-116">Add the following markup inside the **\<body>** tags:</span></span>

   ```html
   <input type="button" value="Price of 3 sandwiches" onclick="Calculate()"/>
   <br />
   <span id="additionResult"></span>
   ```

## <a name="create-an-ajax-enabled-wcf-service"></a><span data-ttu-id="eaab8-117">AJAX etkin bir WCF hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="eaab8-117">Create an AJAX-enabled WCF service</span></span>

1. <span data-ttu-id="eaab8-118">SandwichServices projeye sağ **Çözüm Gezgini** seçip **Ekle** > **yeni öğe**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-118">Right-click the SandwichServices project in **Solution Explorer** and select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="eaab8-119">İçinde **Yeni Öğe Ekle** iletişim kutusunda Genişlet **yüklü** > **Visual C#** > **Web** kategorisi ve ardından seçin **WCF Hizmeti (AJAX etkin)** şablonu.</span><span class="sxs-lookup"><span data-stu-id="eaab8-119">In the **Add New Item** dialog, expand the **Installed** > **Visual C#** > **Web** category, and then select the **WCF Service (AJAX-enabled)** template.</span></span>

   ![Visual Studio'da WCF Hizmeti (AJAX etkin) öğe şablonu](media/create-an-ajax-wcf-asp-net-client/add-wcf-service.png)

1. <span data-ttu-id="eaab8-121">Hizmet adı **CostService** seçip **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-121">Name the service **CostService** and then select **Add**.</span></span>

   <span data-ttu-id="eaab8-122">*CostService.svc.cs* düzenleyicisinde açılır.</span><span class="sxs-lookup"><span data-stu-id="eaab8-122">*CostService.svc.cs* opens in the editor.</span></span>

1. <span data-ttu-id="eaab8-123">İşlem hizmette uygulayın.</span><span class="sxs-lookup"><span data-stu-id="eaab8-123">Implement the operation in the service.</span></span> <span data-ttu-id="eaab8-124">Sandwiches miktarı maliyetini hesaplamak için CostService sınıfına aşağıdaki yöntemi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eaab8-124">Add the following method to the CostService class to calculate the cost of a quantity of sandwiches:</span></span>

    ```csharp
    [OperationContract]
    public double CostOfSandwiches(int quantity)
    {
        return 1.25 * quantity;
    }
    ```

## <a name="configure-the-client-to-access-the-service"></a><span data-ttu-id="eaab8-125">Hizmete erişmek için istemciyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="eaab8-125">Configure the client to access the service</span></span>

1. <span data-ttu-id="eaab8-126">Açık *WebForm1.aspx* seçin ve dosya **tasarım** görünümü.</span><span class="sxs-lookup"><span data-stu-id="eaab8-126">Open the *WebForm1.aspx* file and select the **Design** view.</span></span>

2. <span data-ttu-id="eaab8-127">Gelen **görünümü** menüsünde **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-127">From the **View** menu, select **Toolbox**.</span></span>

3. <span data-ttu-id="eaab8-128">Genişletin **AJAX uzantıları** düğüm ve sürükle ve bırak bir **ScriptManager** forma.</span><span class="sxs-lookup"><span data-stu-id="eaab8-128">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** onto the form.</span></span>

4. <span data-ttu-id="eaab8-129">Geri **kaynak** görüntülemek için arasına aşağıdaki kodu ekleyin  **\<ScriptManager >** WCF Hizmeti yolunu belirtmek için etiketler:</span><span class="sxs-lookup"><span data-stu-id="eaab8-129">Back in the **Source** view, add the following code between the **\<ScriptManager>** tags to specify the path to the WCF service:</span></span>

    ```html
    <Services>
       <asp:ServiceReference Path="~/CostService.svc" />
    </Services>
    ```

1. <span data-ttu-id="eaab8-130">Javascript işlevi için kod ekleme `Calculate()`.</span><span class="sxs-lookup"><span data-stu-id="eaab8-130">Add the code for the Javascript function `Calculate()`.</span></span> <span data-ttu-id="eaab8-131">Aşağıdaki kodda yerleştirin **baş** web formu bölümünü:</span><span class="sxs-lookup"><span data-stu-id="eaab8-131">Place the following code in the **head** section of the web form:</span></span>

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

   <span data-ttu-id="eaab8-132">Bu kod üç sandwiches fiyatı hesaplamak için CostService yöntemini çağırır ve sonucu adı verilen yayılımda görüntüler **additionResult**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-132">This code calls the method of CostService to calculate the price for three sandwiches, and then displays the result in the span called **additionResult**.</span></span>

## <a name="run-the-program"></a><span data-ttu-id="eaab8-133">Programı çalıştırın</span><span class="sxs-lookup"><span data-stu-id="eaab8-133">Run the program</span></span>

<span data-ttu-id="eaab8-134">Emin olun *WebForm1.aspx* odaklı ve tuşuna **Başlat** web istemcisi için düğme.</span><span class="sxs-lookup"><span data-stu-id="eaab8-134">Make sure that *WebForm1.aspx* has focus, and then press **Start** button to launch the web client.</span></span> <span data-ttu-id="eaab8-135">Düğme yeşil üçgenle sahip ve aşağıdaki gibi diyor. **IIS Express (Microsoft Edge)**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-135">The button has a green triangle and says something like **IIS Express (Microsoft Edge)**.</span></span> <span data-ttu-id="eaab8-136">Ya da basabilirsiniz **F5**.</span><span class="sxs-lookup"><span data-stu-id="eaab8-136">Or, you can press **F5**.</span></span> <span data-ttu-id="eaab8-137">Tıklayın **3 sandwiches fiyatı** beklenen çıktıyı "3,75" oluşturmak için düğme.</span><span class="sxs-lookup"><span data-stu-id="eaab8-137">Click the **Price of 3 sandwiches** button to generate the expected output of "3.75".</span></span>

## <a name="example-code"></a><span data-ttu-id="eaab8-138">Örnek kod</span><span class="sxs-lookup"><span data-stu-id="eaab8-138">Example code</span></span>

<span data-ttu-id="eaab8-139">Tam kod aşağıdadır *CostService.svc.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="eaab8-139">Following is the full code in the *CostService.svc.cs* file :</span></span>

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

<span data-ttu-id="eaab8-140">Aşağıdadır tam içeriğini *WebForm1.aspx* sayfası:</span><span class="sxs-lookup"><span data-stu-id="eaab8-140">Following is the full contents of the *WebForm1.aspx* page:</span></span>

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
