---
title: "Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafa15129e4a131c5f50eb3296a87fc141e1bda6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>Nasıl yapılır: AJAX Etkin Bir WCF Hizmeti ve Hizmete Erişen Bir ASP.NET İstemcisi Oluşturma
Bu konuda AJAX etkinleştirilmiş oluşturmak için Visual Studio 2008 kullanmayı gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti ve hizmete erişen bir ASP.NET istemcisi. İstemci ve hizmet için kod bunları oluşturma adımlarını yordamları bölümünde açıklanan sonra örnek bölümünde sağlanır.  
  
### <a name="to-create-the-aspnet-client-application"></a>ASP.NET istemci uygulaması oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Gelen **dosya** menüsünde, select **yeni**, ardından **proje**, ardından **Web**ve ardından **ASP.NET Web uygulaması**.  
  
3.  Proje adı `SandwichServices` tıklatıp **Tamam**.  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>WCF AJAX etkin bir hizmet oluşturmak için  
  
1.  Sağ `SandwichServices` proje **Çözüm Gezgini** penceresini açın ve seçin **Ekle**, ardından **yeni öğe**ve ardından **AJAX etkinleştirilmiş WCF Hizmeti** .  
  
2.  Ad hizmeti `CostService` içinde **adı** kutusuna ve tıklatın **Ekle**.  
  
3.  CostService.svc.cs dosyasını açın.  
  
4.  Belirtin `Namespace` için <xref:System.ServiceModel.ServiceContractAttribute> olarak `SandwichService`:  
  
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
  
5.  İşlem hizmetinde uygulayın. Ekleme <xref:System.ServiceModel.OperationContractAttribute> her sözleşmesinin bir parçası olduğunu belirtmek için işlemlerinin. Aşağıdaki örnek sandviç belirli miktarda maliyetini döndüren bir yöntem uygular.  
  
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
  
### <a name="to-configure-the-client-to-access-the-service"></a>Hizmete erişmek üzere istemciyi yapılandırmak için  
  
1.  Default.aspx sayfasını açın ve seçin **tasarım** görünümü.  
  
2.  Gelen **Görünüm** menüsünde, select **araç**.  
  
3.  Genişletme **AJAX uzantıları** düğümü ve sürükle ve bırak bir **ScriptManager** Default.aspx sayfasını açın.  
  
4.  Sağ **ScriptManager** seçip **özellikleri**.  
  
5.  Genişletme **Hizmetleri** koleksiyonunda **özellikleri** penceresini **ServiceReference Koleksiyonu Düzenleyicisi** penceresi.  
  
6.  Tıklatın **Ekle**, belirtin `CostService.svc` olarak **yolu** tıklayın ve başvurulan **Tamam**.  
  
7.  Genişletme **HTML** düğümünde **araç** ve sürükle ve bırak bir **giriş (düğme)** Default.aspx sayfasını açın.  
  
8.  Sağ **düğmesini** seçip **özellikleri**.  
  
9. Değişiklik **değeri** alanı `Price for 3 Sandwiches`.  
  
10. Çift **düğmesini** JavaScript kodu erişmek için.  
  
11. Şu JavaScript kodunu içinde geçirmek <`script`> öğesi.  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>İstemciden hizmete erişmek için  
  
1.  Hizmet ve Web istemcisi başlatmak için CTRL + F5'ı kullanın. Tıklatın **3 Grilled sandviç fiyatı** "3,75" beklenen çıktı üretmek için düğmesi.  
  
## <a name="example"></a>Örnek  
 Bu örnek WCFService.svc.cs dosyasında yer alan hizmet kodu ve Default.aspx dosyasında yer alan istemci kodu içerir.  
  
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
