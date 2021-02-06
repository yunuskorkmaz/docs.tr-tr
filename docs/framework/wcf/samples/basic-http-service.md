---
description: 'Daha fazla bilgi edinin: temel HTTP hizmeti'
title: Temel HTTP Hizmeti
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 5ac0011b98dd9c4d04d1cf049d31567edae5b2b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632184"
---
# <a name="basic-http-service"></a>Temel HTTP Hizmeti

Bu örnek, Windows Communication Foundation (WCF) REST programlama modelini kullanarak "POX" (düz eski XML) hizmeti olarak adlandırılan HTTP tabanlı, RPC tabanlı bir hizmetin nasıl uygulanacağını gösterir. Bu örnek iki bileşenden oluşur: şirket içinde barındırılan bir WCF HTTP hizmeti (Service.cs) ve hizmeti oluşturan ve ona çağrılar yapan bir konsol uygulaması (Program.cs).

## <a name="sample-details"></a>Örnek Ayrıntılar

WCF hizmeti, `EchoWithGet` `EchoWithPost` giriş olarak geçirilmiş olan dizeyi döndüren 2 işlem sunar.

İşlem, `EchoWithGet` ile birlikte açıklanmış ve <xref:System.ServiceModel.Web.WebGetAttribute> Bu işlem, işlemin http isteklerini işleyeceği anlamına gelir `GET` . <xref:System.ServiceModel.Web.WebGetAttribute>Açıkça bir olarak belirtmediği için <xref:System.UriTemplate> , işlem giriş dizesinin adı olan bir sorgu dizesi parametresi kullanılarak geçirilmesini bekler `s` . Hizmetin beklediği URI biçiminin özelliği kullanılarak özelleştirildiğini unutmayın <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> .

İşlem, `EchoWithPost` <xref:System.ServiceModel.Web.WebInvokeAttribute> bir `GET` işlem olmadığını (yan etkilere sahiptir) gösteren ile birlikte açıklanmış. <xref:System.ServiceModel.Web.WebInvokeAttribute>Açıkça bir olarak belirtmediği için `Method` işlem, `POST` istek GÖVDESINDE dize içeren http isteklerini işler (örneğin, XML biçiminde). İstek için HTTP yönteminin ve URI biçiminin, <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> sırasıyla ve özellikleri kullanılarak özelleştirilemeyeceğini unutmayın <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> .

App.config dosyası, WCF hizmetini <xref:System.ServiceModel.Description.WebHttpEndpoint> <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> özelliği olarak ayarlanmış bir varsayılan ile yapılandırır `true` . Sonuç olarak, WCF altyapısı, `http://localhost:8000/Customers/help` HIZMETINDE http isteklerinin nasıl oluşturulacağı ve HIZMETIN HTTP yanıtının nasıl kullanılacağı hakkında bilgi sağlayan bir OTOMATIK HTML tabanlı yardım sayfası oluşturur.

Program.cs, bir WCF kanal fabrikasının hizmete çağrı yapmak ve yanıtları işlemek için nasıl kullanılabileceğini gösterir. Bu, bir WCF hizmetine erişmenin yalnızca bir yoludur. Ayrıca, ve gibi diğer .NET Framework sınıfları kullanılarak hizmete erişmek da mümkündür <xref:System.Net.HttpWebRequest> <xref:System.Net.WebClient> .

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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
