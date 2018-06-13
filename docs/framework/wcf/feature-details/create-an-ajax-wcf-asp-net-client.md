---
title: 'Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma'
ms.date: 03/30/2017
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 58971d11ab76112627dd81d53381236932268e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490636"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="e49a4-102">Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e49a4-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>
<span data-ttu-id="e49a4-103">Bu konu, Visual Studio 2008 bir AJAX etkinleştirilmiş Windows Communication Foundation (WCF) hizmetini ve hizmete erişen bir ASP.NET istemcisi oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e49a4-103">This topic shows how to use Visual Studio 2008 to create an AJAX-enabled Windows Communication Foundation (WCF) service and an ASP.NET client that accesses the service.</span></span> <span data-ttu-id="e49a4-104">İstemci ve hizmet için kod bunları oluşturma adımlarını yordamları bölümünde açıklanan sonra örnek bölümünde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e49a4-104">The code for the service and for the client are provided in the Example section after the steps for creating them are described in the Procedures section.</span></span>  
  
### <a name="to-create-the-aspnet-client-application"></a><span data-ttu-id="e49a4-105">ASP.NET istemci uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e49a4-105">To create the ASP.NET client application</span></span>  
  
1.  <span data-ttu-id="e49a4-106">Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e49a4-106">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="e49a4-107">Gelen **dosya** menüsünde, select **yeni**, ardından **proje**, ardından **Web**ve ardından **ASP.NET Web uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-107">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Application**.</span></span>  
  
3.  <span data-ttu-id="e49a4-108">Proje adı `SandwichServices` tıklatıp **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-108">Name the Project `SandwichServices` and click **OK**.</span></span>  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a><span data-ttu-id="e49a4-109">WCF AJAX etkin bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e49a4-109">To create the WCF AJAX-enabled service</span></span>  
  
1.  <span data-ttu-id="e49a4-110">Sağ `SandwichServices` proje **Çözüm Gezgini** penceresini açın ve seçin **Ekle**, ardından **yeni öğe**ve ardından **AJAX etkinleştirilmiş WCF Hizmeti** .</span><span class="sxs-lookup"><span data-stu-id="e49a4-110">Right-click the `SandwichServices` project in the **Solution Explorer** window and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="e49a4-111">Ad hizmeti `CostService` içinde **adı** kutusuna ve tıklatın **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-111">Name the service `CostService` in the **Name** box and click **Add**.</span></span>  
  
3.  <span data-ttu-id="e49a4-112">CostService.svc.cs dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e49a4-112">Open the CostService.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="e49a4-113">Belirtin `Namespace` için <xref:System.ServiceModel.ServiceContractAttribute> olarak `SandwichService`:</span><span class="sxs-lookup"><span data-stu-id="e49a4-113">Specify the `Namespace` for <xref:System.ServiceModel.ServiceContractAttribute> as `SandwichService`:</span></span>  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  <span data-ttu-id="e49a4-114">İşlem hizmetinde uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e49a4-114">Implement the operations in the service.</span></span> <span data-ttu-id="e49a4-115">Ekleme <xref:System.ServiceModel.OperationContractAttribute> her sözleşmesinin bir parçası olduğunu belirtmek için işlemlerinin.</span><span class="sxs-lookup"><span data-stu-id="e49a4-115">Add the <xref:System.ServiceModel.OperationContractAttribute> to each of the operations to indicate that they are part of the contract.</span></span> <span data-ttu-id="e49a4-116">Aşağıdaki örnek sandviç belirli miktarda maliyetini döndüren bir yöntem uygular.</span><span class="sxs-lookup"><span data-stu-id="e49a4-116">The following example implements a method that returns the cost of a given quantity of sandwiches.</span></span>  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a><span data-ttu-id="e49a4-117">Hizmete erişmek üzere istemciyi yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="e49a4-117">To configure the client to access the service</span></span>  
  
1.  <span data-ttu-id="e49a4-118">Default.aspx sayfasını açın ve seçin **tasarım** görünümü.</span><span class="sxs-lookup"><span data-stu-id="e49a4-118">Open the Default.aspx page and select the **Design** view.</span></span>  
  
2.  <span data-ttu-id="e49a4-119">Gelen **Görünüm** menüsünde, select **araç**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-119">From the **View** menu, select **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="e49a4-120">Genişletme **AJAX uzantıları** düğümü ve sürükle ve bırak bir **ScriptManager** Default.aspx sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="e49a4-120">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** on to the Default.aspx page.</span></span>  
  
4.  <span data-ttu-id="e49a4-121">Sağ **ScriptManager** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-121">Right-click the **ScriptManager** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="e49a4-122">Genişletme **Hizmetleri** koleksiyonunda **özellikleri** penceresini **ServiceReference Koleksiyonu Düzenleyicisi** penceresi.</span><span class="sxs-lookup"><span data-stu-id="e49a4-122">Expand the **Services** collection in the **Properties** window to open up the **ServiceReference Collection Editor** window.</span></span>  
  
6.  <span data-ttu-id="e49a4-123">Tıklatın **Ekle**, belirtin `CostService.svc` olarak **yolu** tıklayın ve başvurulan **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-123">Click **Add**, specify `CostService.svc` as the **Path** referenced, and click **OK**.</span></span>  
  
7.  <span data-ttu-id="e49a4-124">Genişletme **HTML** düğümünde **araç** ve sürükle ve bırak bir **giriş (düğme)** Default.aspx sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="e49a4-124">Expand the **HTML** node in the **Toolbox** and drag and drop an **Input (Button)** on to the Default.aspx page.</span></span>  
  
8.  <span data-ttu-id="e49a4-125">Sağ **düğmesini** seçip **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e49a4-125">Right-click the **Button** and select **Properties**.</span></span>  
  
9. <span data-ttu-id="e49a4-126">Değişiklik **değeri** alanı `Price for 3 Sandwiches`.</span><span class="sxs-lookup"><span data-stu-id="e49a4-126">Change the **Value** field to `Price for 3 Sandwiches`.</span></span>  
  
10. <span data-ttu-id="e49a4-127">Çift **düğmesini** JavaScript kodu erişmek için.</span><span class="sxs-lookup"><span data-stu-id="e49a4-127">Double-click the **Button** to access the JavaScript code.</span></span>  
  
11. <span data-ttu-id="e49a4-128">Şu JavaScript kodunu içinde geçirmek <`script`> öğesi.</span><span class="sxs-lookup"><span data-stu-id="e49a4-128">Pass in the following JavaScript code within the <`script`> element.</span></span>  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a><span data-ttu-id="e49a4-129">İstemciden hizmete erişmek için</span><span class="sxs-lookup"><span data-stu-id="e49a4-129">To access the service from the client</span></span>  
  
1.  <span data-ttu-id="e49a4-130">Hizmet ve Web istemcisi başlatmak için CTRL + F5'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e49a4-130">Use Ctrl +F5 to launch the service and the Web client.</span></span> <span data-ttu-id="e49a4-131">Tıklatın **3 Grilled sandviç fiyatı** "3,75" beklenen çıktı üretmek için düğmesi.</span><span class="sxs-lookup"><span data-stu-id="e49a4-131">Click the **Price for 3 Grilled Sandwiches** button to generate the expected output of "3.75".</span></span>  
  
## <a name="example"></a><span data-ttu-id="e49a4-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="e49a4-132">Example</span></span>  
 <span data-ttu-id="e49a4-133">Bu örnek WCFService.svc.cs dosyasında yer alan hizmet kodu ve Default.aspx dosyasında yer alan istemci kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="e49a4-133">This example contains the service code contained in the WCFService.svc.cs file and the client code contained in the Default.aspx file.</span></span>  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
```     
