---
title: Şartlı Alma ve Yerleştirme
ms.date: 03/30/2017
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
ms.openlocfilehash: 29819f89327128cdd71cc89eb8d14126522dc2df
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539389"
---
# <a name="conditional-get-and-put"></a>Şartlı Alma ve Yerleştirme
Bu örnek, yeni koşullu almak ve WCF REST programlama modeli için API'leri güncelleştirebiliriz nasıl kullanılacağını gösterir. Koşullu alma ve güncelleştirme için en uygun olduğu için kaynak odaklı ve REST Hizmetleri, bu örnek genişletir [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek. Bu örnek, koşullu alma ve güncelleştirme desteği ekleme odaklanır [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) de kullanıma sunulan yeni API'leri kullanarak örnek [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Gösteriler  
 Koşullu alın ve güncelleştirme  
  
## <a name="discussion"></a>Tartışma  
 Bu örnekte WCF hizmeti kaynak odaklı müşteriler koleksiyonunu ve REST şekilde kullanıma sunar. Hizmet uygulaması ayrıntılı bir açıklaması için lütfen bkz [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek.  
  
 Bu örnek koşullu alma ve güncelleştirme olanağı ekler [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) örnek. Koşullu alabilir ve kullanımı HTTP varlık etiketleri ve istemciler olması veya belirli bir kaynak için en son varlık yok doğrulamak için HTTP If-None-Match ve IF-Match üst bilgileri güncelleştirin. Ancak, HTTP If-None-Match ve IF-Match üst bilgileri doğru bir şekilde ayrıştırmak için kod uygulama sıkıcı ve hataya yatkın olabilir. Bu nedenle, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> ve <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> yöntemler eklenmiştir <xref:System.ServiceModel.Web.IncomingWebRequestContext>, hangi erişilebilir'ün geçerli örneğini kullanarak <xref:System.ServiceModel.Web.WebOperationContext>. Ayrıca, `SetETag` yöntemi eklendi <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, geçerli varlık etiketleri döndürülecek kolaylaştırır.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Yöntemi [WebGet] işlemleri ile kullanılmak üzere tasarlanmıştır. Belirtilen kaynak geçerli varlık etiketi alır `entityTag` olabilen parametresi bir `string`, `int`, `long` veya `Guid`. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Yöntemi varlık etiketi isteğin HTTP If-None-Match üst bilgisi karşı denetler. Varlık etiketi HTTP If-None-Match üst bilgisinde mevcut olması durumunda bir <xref:System.ServiceModel.Web.WebFaultException> ile bir durum kodunu (304) değişiklik oluşturulur; Aksi takdirde yöntemi döndürür. Bu varlık olduğunu buysa sunucuya bildirin ve bu istemcinin zaten yoksa, yalnızca geçerli varlığı göndermek için istemci koşullu alma mekanizması sağlar. Kullanım örneği <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yöntemi görülebilir `GetCustomer` ve `GetCustomers` hizmetinin operations. Bu çağrılar dikkat edin önemlidir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> değil döndürebilir. Böylece istek çağırmadan önce başarılı olması için zaten biliniyor, geliştiricilerin işlemi uygulamanız gerekir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> olan yürütülen, böyle olması durumunda çağrısı <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> olan mevcut hizmet başarılı durum koduyla bir yanıt gönderir.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Yöntemi benzer <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> yöntemi. Ayrıca, belirtilen kaynak için geçerli varlık etiketi alır. Ancak, yöntem "PUT" veya "Sil" ayarlanır [Webınvoke] işlemleri ile kullanılmak üzere tasarlanmıştır. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Yöntemi varlık etiketi isteğin HTTP IF-Match üst karşı denetler. Varlık etiketi HTTP IF-Match üst bilgisinde mevcut değilse bir <xref:System.ServiceModel.Web.WebFaultException> önkoşulu başarısız oldu (412) kodu ile bir durum oluşturulur. İstemciyi bu varlık için kaynak olan buysa sunucuya bildirin ve yalnızca kaynak değiştirmek istemci izin vermek için koşullu bir güncelleştirme mekanizması sağlar; varlık varsa geçerli olur. Kullanım örneği <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> yöntemi görülebilir `UpdateCustomer` ve `DeleteCustomer` hizmetinin operations. Olduğu gibi <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, bu çağrılar dikkat edin önemlidir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> değil döndürebilir. Geliştiriciler çağırmadan önce başarılı olması için istek zaten biliniyor, işlemi uygulamanız gerekir <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> olan yürütülen, böyle olması durumunda çağrısı <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> hizmet başarılı durum kodu ile yanıt mevcut değildi.  
  
 Örnek şirket içinde barındırılan bir hizmet ve içinde bir konsol uygulaması çalıştıran bir istemciyi oluşur. Konsol uygulamasının çalışır gibi istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
1.  Koşullu alın ve Put örnek çözümü açın. Başlatma sırasında [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], örnek başarıyla yürütmek için yönetici olarak çalıştırmanız gerekir. Sağ tıklayarak bunu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] simgesine ve ardından **yönetici olarak çalıştır** bağlam menüsünden.  
  
2.  Çözümü derleyin ve konsol uygulama projesini çalıştırmak için CTRL + F5 tuşuna basın CTRL + SHIFT + B tuşlarına basın. Bu projede hata ayıklama (F5 yerine CTRL + F5 tuşlarına basarak) etkin olan çalıştırılıyorsa, koşullu bir özel durum oluştuğunda hata ayıklayıcıyı durdurur alın ve denetimi yerleştirin. Bu durumda, örnek yürütme devam etmek için F5 tuşuna basın.  
  
3.  Konsol penceresinde görünür kumlarda çalışan hizmeti için çalışan hizmetin URI ve HTML Yardım sayfası URI'sini sağlar.  
  
4.  Örnek çalışırken, istemci hizmete istekler gönderir ve konsol penceresine yanıtları yazar.  
  
5.  Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
