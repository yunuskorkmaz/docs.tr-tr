---
title: "Şartlı Alma ve Yerleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59a9f0638855206f390ee7fbace580ba37e25e23
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="conditional-get-and-put"></a>Şartlı Alma ve Yerleştirme
Bu örnek yeni koşullu almak ve API'ler için WCF REST programlama modeli güncelleştirmek nasıl kullanılacağı gösterilmektedir. Koşullu alın ve güncelleştirme için en uygun olduğundan kaynak odaklı ve REST Hizmetleri, bu örnek genişletir [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek. Koşullu almak ve güncelleştirme desteği eklemek için bu örnek odaklanır [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) sunulan yeni API'leri kullanarak örnek [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Gösteriler  
 Koşullu alın ve güncelleştirme  
  
## <a name="discussion"></a>Tartışma  
 WCF hizmeti bu örnek, bir kaynak odaklı müşteriler koleksiyonunu ve REST şekilde gösterir. Hizmet uygulaması ayrıntılı bir açıklaması için lütfen bkz [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek.  
  
 Bu örnek koşullu alın ve güncelleştirme olanağı ekler [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek. Koşullu almak ve kullanım HTTP varlık etiketleri ve istemcilerin sahip veya belirli bir kaynak için en güncel varlık yok doğrulamak için HTTP If-None-Match ve IF-Match üst bilgileri güncelleştirin. Ancak, doğru HTTP If-None-Match ve IF-Match üst bilgileri ayrıştırmak için kod uygulama yorucu ve hataya yatkın olabilir. Bu nedenle, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> ve <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> yöntemler eklenmiştir <xref:System.ServiceModel.Web.IncomingWebRequestContext>, hangi erişilebilir geçerli örneği kullanarak <xref:System.ServiceModel.Web.WebOperationContext>. Ayrıca, `SetETag` yöntemi eklenmiştir <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, geçerli bir varlık etiketleri döndürülecek kolaylaştırır.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Yöntemi [WebGet] işlemleri ile kullanılmak üzere tasarlanmıştır. Belirtilen kaynak olarak geçerli varlık etiketi alır `entityTag` olabilir parametresi bir `string`, `int`, `long` veya `Guid`. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Yöntemi varlık etiketi isteğin HTTP If-None-Match üstbilgisi karşı denetler. Varlık etiketi HTTP If-None-Match üst bilgisi varsa, sonra bir <xref:System.ServiceModel.Web.WebFaultException> (304) değişiklik kodunu bir durum ile oluşturulur; Aksi takdirde yöntemi döndürür. Koşullu alma mekanizması sunucusuna bu varlık olduğunu bildirir ve bunu istemci zaten yoksa, yalnızca geçerli varlık göndermek için istemcinin verir. Kullanım örneği <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yöntemi içinde görülme `GetCustomer` ve `GetCustomers` hizmetinin operations. Bu çağrılar dikkate almak önemlidir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> değil döndürebilir. Böylece istek çağırmadan önce başarılı olması için zaten biliniyor, geliştiricilerin işlemi uygulamanız gerekir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yürütülen ise böyle olması durumunda çağrısı <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> edildi yok, hizmet başarılı durum koduyla bir yanıt gönderir.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Yöntemi benzer <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yöntemi. Ayrıca, söz konusu kaynağın geçerli varlık etiketi alır. Ancak, yöntem "PUT" veya "DELETE" olarak ayarlanırsa [Webınvoke] işlemleri ile kullanılmak üzere tasarlanmıştır. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Yöntemi varlık etiketi isteğin HTTP IF-Match üstbilgisi karşı denetler. Varlık etiketi HTTP IF-Match üst bilgisinde mevcut değilse sonra bir <xref:System.ServiceModel.Web.WebFaultException> bir durum ile önkoşul başarısız oldu (412) kodunu atılır. Koşullu güncelleştirme mekanizması sunucusuna bu varlık için kaynak olduğunu bildirir ve yalnızca kaynak değiştirmek istemcinin sağlamak için istemcinin verir; varlık varsa geçerli olur. Kullanım örneği <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> yöntemi içinde görülme `UpdateCustomer` ve `DeleteCustomer` hizmetinin operations. İle olarak yalnızca <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, bu çağrılar dikkate almak önemlidir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> değil döndürebilir. Geliştiriciler sağlayacak şekilde istek çağırmadan önce başarılı olması için zaten biliniyor işlemi uygulamanız gerekir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> yürütülen ise böyle olması durumunda çağrısı <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> hizmet başarılı durum koduyla yanıt, yoktu.  
  
 Kendini barındıran hizmet ve bir konsol uygulaması içinde çalıştırılan bir istemciyi, örnek oluşur. Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Koşullu Get ve Put örnek çözümü açın. Başlatılırken [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], örnek başarılı bir şekilde çalıştırmak için yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesi ve seçme **yönetici olarak çalıştır** ve bağlam menüsünden.  
  
2.  Çözümü derlemek ve konsol uygulama projesi çalıştırmak için CTRL + F5 tuşuna basın CTRL + SHIFT + B tuşuna basın. Bu proje (CTRL + F5 yerine F5 tuşuna basarak) etkin hata ayıklama ile çalışıyorsa göre koşullu bir özel durum oluştuğunda hata ayıklayıcı durakları almak ve denetimi yerleştirin. Bu gerçekleştiğinde, örnek yürütme devam etmek için F5 tuşuna basın.  
  
3.  Konsol penceresinde görünür kum çalışan hizmeti için çalışan hizmetin URI ve HTML Yardım sayfası URI'sini sağlar.  
  
4.  Örnek çalışırken, istemci istekleri hizmetine gönderir ve yanıtları konsol penceresine yazar.  
  
5.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
