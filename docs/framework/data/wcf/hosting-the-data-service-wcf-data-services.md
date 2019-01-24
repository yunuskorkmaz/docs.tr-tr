---
title: Veri hizmetini (WCF Veri Hizmetleri) barındırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 1464880e92753d2774b1ca60d55c71a88d8e9b15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519415"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Veri hizmetini (WCF Veri Hizmetleri) barındırma
WCF veri hizmetlerini kullanarak, verileri olarak kullanıma sunan bir hizmet oluşturabilmeniz için bir [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] akış. Bu veri hizmeti öğesinden devralınan bir sınıf olarak tanımlanan <xref:System.Data.Services.DataService%601>. Bu sınıf, OData gerektirdiği yanıt iletilerini istek iletilerini işlemek ve güncelleştirmeleri veri kaynağına karşı gerçekleştirmek için gereken işlevleri sağlar. Ancak, bir veri hizmeti bağlamak ve bir ağ yuvayı için gelen HTTP istek dinleyemedi. Bu gerekli işlevselliği için veri hizmetini barındıran bir bileşende kullanır.

 Veri Hizmeti ana veri hizmeti adına aşağıdaki görevleri gerçekleştirir:

-   İsteklerini dinler ve bu istekleri veri hizmetine yönlendirir.

-   Her istek için veri Hizmeti'nin bir örneğini oluşturur.

-   İstekleri veri hizmeti gelen isteği işleyemedi.

-   Veri hizmeti adına yanıtı gönderir.

 Veri hizmetini barındıran basitleştirmek için WCF Veri Hizmetleri Windows Communication Foundation (WCF) ile tümleştirmek için tasarlanmıştır. Veri Hizmeti ana bilgisayar olarak hizmet veren bir varsayılan WCF uygulaması veri hizmetinin sağladığı bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama. Bu nedenle, aşağıdaki yollardan birinde bir veri hizmeti barındırabilirsiniz:

-   İçinde bir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uygulama.

-   Yönetilen bir uygulamada, şirket içinde barındırılan WCF hizmetleri destekler.

-   Bazı diğer özel veri hizmeti ana bilgisayar.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Bir ASP.NET uygulamasında veri hizmeti barındırma

Kullanırken **Yeni Öğe Ekle** iletişim Aracı'nı bir ASP.NET uygulamasında veri hizmeti tanımlamak için Visual Studio 2015'te, projede iki yeni dosya oluşturur. İlk dosya bir `.svc` uzantısı ve veri hizmeti örneği oluşturmak nasıl WCF çalıştırma zamanı bildirir. Tamamlandığında, oluşturulan Northwind örnek veri hizmeti için bu dosyanın bir örneği verilmiştir [hızlı](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md):

```
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Bu yönerge kullanarak hizmet ana bilgisayarı için adlandırılmış veri hizmeti sınıfındaki oluşturmak için uygulama bildirir <xref:System.Data.Services.DataServiceHostFactory> sınıfı.

 Arka plan kod sayfası `.svc` dosyası gibi Northwind örnek veri hizmeti için tanımlanan veri hizmetinin kendisi, uygulama sınıfı içerir:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]

 Bir veri hizmeti bir WCF hizmeti gibi davranan olduğundan, veri hizmeti ile tümleşir [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ve WCF Web programlama modelini kullanır. Daha fazla bilgi için [WCF hizmetleri ve ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web HTTP programlama modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>Şirket içinde barındırılan WCF hizmetleri
 WCF uygulaması içerir olduğundan, bir veri hizmetine bir WCF hizmeti olarak kendi kendine barındırma WCF veri hizmetleri destekler. Bir hizmet, tüm şirket içinde barındırılan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bir konsol uygulaması gibi uygulama. <xref:System.Data.Services.DataServiceHost> Öğesinden devralan sınıf <xref:System.ServiceModel.Web.WebServiceHost>, belirli bir adresten veri hizmeti örneklemek için kullanılır.

 Bu, dağıtmak ve hizmette sorun gidermek kolaylaştırabilir çünkü kendi kendine barındırma geliştirme ve test için kullanılabilir. Ancak, bu tür barındırma tarafından sağlanan Gelişmiş barındırma ve yönetim özellikleri sağlamaz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] veya Internet Information Services (IIS) tarafından. Daha fazla bilgi için [yönetilen bir uygulamada barındırma](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Bir özel veri hizmeti ana bilgisayarı tanımlama
 WCF konak uygulama çok kısıtlayıcı olduğu durumlarda, veri hizmeti için özel bir ana bilgisayar da tanımlayabilirsiniz. Uygulayan sınıfa <xref:System.Data.Services.IDataServiceHost> arabirimi kullanılabilir ağ ana bilgisayarı için bir veri hizmeti. Özel bir ana bilgisayar uygulamalıdır <xref:System.Data.Services.IDataServiceHost> arabirim ve veri hizmeti ana bilgisayarının aşağıdaki temel sorumluluklarını işleyebilir:

-   Veri hizmetinin Hizmet kök yoluyla sağlar.

-   İşlem istek ve yanıt üst bilgileri uygun <xref:System.Data.Services.IDataServiceHost> üye uygulaması.

-   Veri Hizmeti tarafından oluşturulan özel durumları işler.

-   Sorgu dizesi parametreleri doğrulayın.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [Verilerinizi Hizmet Olarak Kullanıma Sunma](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
- [Veri Hizmeti Yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
