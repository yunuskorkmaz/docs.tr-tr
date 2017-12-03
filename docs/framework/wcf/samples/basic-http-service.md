---
title: Temel HTTP Hizmeti
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9da2addce9c837499783664bb3b1417d30b937b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="basic-http-service"></a>Temel HTTP Hizmeti
Bu örnek, özellik "POX" (düz eski XML) hizmet vermek için başvurulan – kullanarak bir HTTP tabanlı, RPC tabanlı hizmeti - uygulama gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST programlama modeli. Bu örnek iki bileşenden oluşur: kendini barındıran [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP hizmet (adını da) ve hizmet oluşturur ve bunu çağrılar bir konsol uygulaması (Program.cs).  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet sunan 2 işlemleri `EchoWithGet` ve `EchoWithPost`, girdi olarak geçirilen dize döndürür.  
  
 `EchoWithGet` İşlemi açıklama ile <xref:System.ServiceModel.Web.WebGetAttribute>, belirten işlemi HTTP işler `GET` istekleri. Çünkü <xref:System.ServiceModel.Web.WebGetAttribute> açıkça belirtmediği bir <xref:System.UriTemplate>, ada sahip bir sorgu dizesi parametresi kullanımında geçirilecek giriş dizesi işlemi bekliyor `s`. Hizmet bekliyor URI biçimi kullanılarak özelleştirilebilir Not <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> özelliği.  
  
 `EchoWithPost` İşlemi açıklama ile <xref:System.ServiceModel.Web.WebInvokeAttribute>, bunu belirten değil bir `GET` işlemi (yan etkisi yoktur). Çünkü <xref:System.ServiceModel.Web.WebInvokeAttribute> açıkça belirtmediği bir `Method`, işlemi işleyen HTTP `POST` istek gövdesinde dizesine sahip istekleri (XML biçiminde örneği için). HTTP yöntemi ve istek için URI biçimi kullanılarak özelleştirilebilir olduğunu unutmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> ve <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> özellikleri sırasıyla.  
  
 App.config dosyasını WCF Hizmeti ile bir varsayılan yapılandırır <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliğini `true`. Sonuç olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapıyı oluşturur otomatik bir HTML tabanlı yardım sayfasına `http://localhost:8000/Customers/help` HTTP isteklerine hizmet oluşturmak ve hizmetin HTTP yanıtı kullanma hakkında bilgi sağlar.  
  
 Program.cs gösteren nasıl bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal fabrikası, hizmet ve işlem yanıtları çağrı yapmak için kullanılabilir. Bu yalnızca bir erişmek için yolu olduğuna dikkat edin bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet. Diğer .NET Framework sınıfları gibi kullanarak hizmete erişmek mümkündür <xref:System.Net.HttpWebRequest> ve <xref:System.Net.WebClient>. SDK'sındaki diğer örnekleri (gibi [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek ve [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek) ile iletişim kurmak için bu sınıfları kullanmayı gösteren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.  
  
 Kendini barındıran hizmet ve bir istemci örnek oluşan her ikisi içinde bir konsol uygulamasını çalıştırın. Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Çözümü için temel Http hizmeti örneği açın. Başlatılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], başarılı bir şekilde çalıştırmak için örnek yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesini ve seçerek **yönetici olarak çalıştır** ve bağlam menüsünden.  
  
2.  Çözümü derlemek ve hata ayıklama olmadan konsol uygulamasını çalıştırmak için Ctrl + F5 tuşuna basın CTRL + SHIFT + B tuşuna basın. Konsol penceresinde görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur. Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
3.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [Temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md)
