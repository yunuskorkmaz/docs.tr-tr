---
title: Temel HTTP Hizmeti
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: ec716b41efb3dde6e5afdb386d797e402d924b56
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045154"
---
# <a name="basic-http-service"></a>Temel HTTP Hizmeti

Bu örnek, Windows Communication Foundation (WCF) REST programlama modelini kullanarak "POX" (düz eski XML) hizmeti olarak adlandırılan HTTP tabanlı, RPC tabanlı bir hizmetin nasıl uygulanacağını gösterir. Bu örnek iki bileşenden oluşur: şirket içinde barındırılan bir WCF HTTP hizmeti (Service.cs) ve hizmeti oluşturan ve ona çağrılar yapan bir konsol uygulaması (Program.cs).

## <a name="sample-details"></a>Örnek Ayrıntılar

WCF hizmeti, giriş olarak geçirilmiş olan `EchoWithGet` dizeyi `EchoWithPost`döndüren 2 işlem sunar.

İşlem, ile birlikte <xref:System.ServiceModel.Web.WebGetAttribute>açıklanmış ve bu işlem, işlemin http `GET` isteklerini işleyeceği anlamına gelir. `EchoWithGet` Açıkça bir <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.UriTemplate>olarak belirtmediği için, işlem giriş dizesinin adı `s`olan bir sorgu dizesi parametresi kullanılarak geçirilmesini bekler. Hizmetin beklediği URI biçiminin <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> özelliği kullanılarak özelleştirildiğini unutmayın.

İşlem, <xref:System.ServiceModel.Web.WebInvokeAttribute> bir`GET` işlem olmadığını (yan etkilere sahiptir) gösteren ile birlikte açıklanmış. `EchoWithPost` Açıkça bir <xref:System.ServiceModel.Web.WebInvokeAttribute> `Method`olarak belirtmediği için işlem, istek gövdesinde dize içeren `POST` http isteklerini işler (örneğin, XML biçiminde). İstek için http yönteminin ve URI biçiminin, sırasıyla <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> ve <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> özellikleri kullanılarak özelleştirilemeyeceğini unutmayın.

App. config dosyası, WCF hizmetini <xref:System.ServiceModel.Description.WebHttpEndpoint> <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliği olarak `true`ayarlanmış bir varsayılan ile yapılandırır. Sonuç olarak, WCF altyapısı, hizmetinde http isteklerinin nasıl oluşturulacağı ve hizmetin HTTP yanıtının `http://localhost:8000/Customers/help` nasıl kullanılacağı hakkında bilgi sağlayan bir otomatik HTML tabanlı yardım sayfası oluşturur.

Program.cs, bir WCF kanal fabrikasının hizmete çağrı yapmak ve yanıtları işlemek için nasıl kullanılabileceğini gösterir. Bu, bir WCF hizmetine erişmenin yalnızca bir yoludur. Ayrıca, ve <xref:System.Net.HttpWebRequest> <xref:System.Net.WebClient>gibi diğer .NET Framework sınıfları kullanılarak hizmete erişmek da mümkündür.

Örnek, kendi kendine barındırılan bir hizmet ve her ikisinin de bir konsol uygulaması içinde çalıştırdığı bir istemcisinden oluşur. Konsol uygulaması çalışırken, istemci hizmete istekler yapar ve ilgili bilgileri, yanıtlardan konsol penceresine yazar.

#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için

1. Temel http hizmeti örneği için çözümü açın. Visual Studio 2012 ' ı başlatırken, örneğin başarıyla yürütülmesi için yönetici olarak çalıştırmanız gerekir. Bunu, Visual Studio 2012 simgesine sağ tıklayıp bağlam menüsünden **yönetici olarak çalıştır** ' ı seçerek yapın.

2. Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın ve ardından CTRL + F5 tuşlarına basarak konsol uygulamasını hata ayıklama olmadan çalıştırın. Konsol penceresi görünür ve çalışan hizmet için HTML yardım sayfasının URI 'sini ve çalıştıran hizmeti sağlar. Herhangi bir noktada, yardım sayfasının URI 'sini bir tarayıcıda yazarak HTML yardım sayfasını görüntüleyebilirsiniz. Örnek çalışırken, istemci geçerli etkinliğin durumunu yazar.

3. Örneği sonlandırmak için herhangi bir tuşa basın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
