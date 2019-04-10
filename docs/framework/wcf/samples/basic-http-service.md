---
title: Temel HTTP Hizmeti
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 247fedac339ebb22a6ef3b3e84f557451ecaaf1a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337116"
---
# <a name="basic-http-service"></a>Temel HTTP Hizmeti
Bu örnek, bu özellik Windows Communication Foundation (WCF) REST programlama modeli kullanarak "POX" (düz eski XML) hizmet olarak – başvurulan bir HTTP tabanlı, RPC tabanlı hizmeti - uygulama gösterilmiştir. Bu örnek iki bileşenden oluşur: şirket içinde barındırılan bir WCF HTTP hizmet (adını da) ve hizmet oluşturur ve bu çağrıları yapan bir konsol uygulaması (Program.cs).  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 2 işlemleri, WCF hizmeti sunan `EchoWithGet` ve `EchoWithPost`, giriş olarak geçirilen bir dize döndürür.  
  
 `EchoWithGet` İşlemi ile ek açıklamalı <xref:System.ServiceModel.Web.WebGetAttribute>, gösteren işlemi HTTP işler `GET` istekleri. Çünkü <xref:System.ServiceModel.Web.WebGetAttribute> açıkça belirtmediği bir <xref:System.UriTemplate>, Giriş dizesinin ada sahip bir sorgu dizesi parametresi kullanarak geçirilecek işlemi bekliyor `s`. Hizmet bekliyor URI biçimi kullanılarak özelleştirilebilir Not <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> özelliği.  
  
 `EchoWithPost` İşlemi ile ek açıklamalı <xref:System.ServiceModel.Web.WebInvokeAttribute>, bunu belirten değil bir `GET` işlemi (yan etkileri vardır). Çünkü <xref:System.ServiceModel.Web.WebInvokeAttribute> açıkça belirtmediği bir `Method`, işlemi işleyen HTTP `POST` istek gövdesinde bir dize içeren istekleri (XML biçiminde örneği için). HTTP yöntemi ve istek için URI biçimi kullanılarak özelleştirilebilir olduğunu unutmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> ve <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> özellikleri sırasıyla.  
  
 App.config dosyasını WCF Hizmeti ile bir varsayılan yapılandırır <xref:System.ServiceModel.Description.WebHttpEndpoint> olan <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliğini `true`. Sonuç olarak, WCF altyapısı bir otomatik dayalı HTML Yardım sayfası oluşturur `http://localhost:8000/Customers/help` HTTP isteklerine hizmet oluşturmak ve hizmetin HTTP yanıtı kullanma hakkında bilgi sağlar.  
  
 Program.cs WCF kanal fabrikası hizmet ve işlem yanıtları çağrı yapmak için nasıl kullanılabileceğini gösterir. Bir WCF Hizmeti erişmek için yalnızca bir yol olduğunu unutmayın. Diğer .NET Framework sınıflarını gibi hizmete erişmek mümkündür <xref:System.Net.HttpWebRequest> ve <xref:System.Net.WebClient>.
  
 Örnek şirket içinde barındırılan bir hizmet ve istemci oluşur. her ikisi de bir konsol uygulaması içinde çalıştırın. Konsol uygulamasının çalışır gibi istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1. Temel Http hizmeti örneği için çözümü açın. Visual Studio 2012 başlatırken başarıyla yürütmek için örnek için yönetici olarak çalıştırmanız gerekir. Visual Studio 2012 simgesini sağ tıklatıp seçerek bunu **yönetici olarak çalıştır** bağlam menüsünden.  
  
2. Çözümü derleyin ve konsol uygulamasının hata ayıklama olmadan çalıştırmak için Ctrl + F5 tuşuna basın CTRL + SHIFT + B tuşlarına basın. Konsol penceresinde görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti. Herhangi bir noktada HTML Yardım sayfası URI Yardım sayfasının bir tarayıcıda yazarak görüntüleyebilirsiniz. Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.  
  
3. Örnek sonlandırmak için herhangi bir tuşa basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
