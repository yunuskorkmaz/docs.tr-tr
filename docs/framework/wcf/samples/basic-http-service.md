---
title: Temel HTTP Hizmeti
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 8dfcd5a751bcef6aa24b5cb4a200c8820c43fe81
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716099"
---
# <a name="basic-http-service"></a>Temel HTTP Hizmeti

Bu örnek, Windows Communication Foundation (WCF) REST programlama modelini kullanarak "POX" (düz eski XML) hizmeti olarak adlandırılan HTTP tabanlı, RPC tabanlı bir hizmetin nasıl uygulanacağını gösterir. Bu örnek iki bileşenden oluşur: şirket içinde barındırılan bir WCF HTTP hizmeti (Service.cs) ve hizmeti oluşturan ve ona çağrılar yapan bir konsol uygulaması (Program.cs).

## <a name="sample-details"></a>Örnek Ayrıntılar

WCF hizmeti, giriş olarak geçirilmiş dizeyi döndüren 2 işlem, `EchoWithGet` ve `EchoWithPost`sunar.

`EchoWithGet` işlemine, işlemin HTTP `GET` isteklerini işlediğini gösteren <xref:System.ServiceModel.Web.WebGetAttribute>ile açıklama eklenir. <xref:System.ServiceModel.Web.WebGetAttribute> açıkça bir <xref:System.UriTemplate>belirtmediğinden, işlem giriş dizesinin `s`adında bir sorgu dizesi parametresi kullanılarak geçirilmesini bekler. Hizmetin beklediği URI biçiminin <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> özelliği kullanılarak özelleştirildiğini unutmayın.

`EchoWithPost` işlemine <xref:System.ServiceModel.Web.WebInvokeAttribute>açıklanmış ve bu bir `GET` işlemi olmadığını (yan etkilere sahiptir) gösterir. <xref:System.ServiceModel.Web.WebInvokeAttribute> açıkça bir `Method`belirtmediğinden, işlem, istek gövdesinde dize içeren HTTP `POST` isteklerini (örneğin, XML biçiminde) işler. HTTP yönteminin ve isteğin URI 'sinin biçiminin sırasıyla <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> ve <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> özellikleri kullanılarak özelleştirildiğini unutmayın.

App. config dosyası, WCF hizmetini <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliği `true`olarak ayarlanmış bir varsayılan <xref:System.ServiceModel.Description.WebHttpEndpoint> ile yapılandırır. Sonuç olarak, WCF altyapısı, hizmete HTTP isteklerinin nasıl oluşturulacağı ve hizmetin HTTP yanıtının nasıl kullanılacağı hakkında bilgi sağlayan `http://localhost:8000/Customers/help` adresinde otomatik bir HTML tabanlı yardım sayfası oluşturur.

Program.cs, bir WCF kanal fabrikasının hizmete çağrı yapmak ve yanıtları işlemek için nasıl kullanılabileceğini gösterir. Bu, bir WCF hizmetine erişmenin yalnızca bir yoludur. Ayrıca, <xref:System.Net.HttpWebRequest> ve <xref:System.Net.WebClient>gibi diğer .NET Framework sınıfları kullanılarak hizmete erişmek da mümkündür.

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
