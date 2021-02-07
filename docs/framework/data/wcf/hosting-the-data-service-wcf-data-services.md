---
description: 'Hakkında daha fazla bilgi edinin: veri hizmetini barındırma (WCF Veri Hizmetleri)'
title: Veri hizmetini barındırma (WCF Veri Hizmetleri)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
- WCF Data Services, Windows Communication Foundation
ms.assetid: b48f42ce-22ce-4f8d-8f0d-f7ddac9125ee
ms.openlocfilehash: 519adde3a3e054d68ff9a1b7acf7ff06c0ca7532
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765795"
---
# <a name="hosting-the-data-service-wcf-data-services"></a>Veri hizmetini barındırma (WCF Veri Hizmetleri)

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

WCF Veri Hizmetleri kullanarak, verileri açık veri Protokolü (OData) akışı olarak sunan bir hizmet oluşturabilirsiniz. Bu veri hizmeti, öğesinden devralan bir sınıf olarak tanımlanır <xref:System.Data.Services.DataService%601> . Bu sınıf, istek iletilerini işlemek, veri kaynağına karşı güncelleştirmeler gerçekleştirmek ve OData için gereken yanıt iletilerini oluşturmak için gereken işlevselliği sağlar. Ancak, bir veri hizmeti gelen HTTP istekleri için bir ağ yuvasına bağlanamaz ve bu yuvayı dinlemez. Bu gerekli işlevsellik için veri hizmeti bir barındırma bileşeni kullanır.

 Veri hizmeti ana bilgisayarı, veri hizmeti adına aşağıdaki görevleri gerçekleştirir:

- İstekleri dinler ve bu istekleri veri hizmetine yönlendirir.

- Her istek için veri hizmetinin bir örneğini oluşturur.

- Veri hizmetinin gelen isteği işlemesini ister.

- Yanıtı veri hizmeti adına gönderir.

 Bir veri hizmetini barındırmayı basitleştirmek için WCF Veri Hizmetleri, Windows Communication Foundation (WCF) ile tümleştirilecek şekilde tasarlanmıştır. Veri hizmeti bir ASP.NET uygulamasında veri hizmeti Konağı görevi gören varsayılan bir WCF uygulaması sağlar. Bu nedenle, aşağıdaki yollarla bir veri hizmetini barındırabilirsiniz:

- Bir ASP.NET uygulamasında.

- Şirket içinde barındırılan WCF hizmetlerini destekleyen bir yönetilen uygulama.

- Diğer bazı özel veri hizmeti ana bilgisayarında.

## <a name="hosting-a-data-service-in-an-aspnet-application"></a>Bir ASP.NET uygulamasında veri hizmeti barındırma

Bir ASP.NET uygulamasında veri hizmeti tanımlamak için Visual Studio 2015 ' de **Yeni öğe Ekle** iletişim kutusunu kullandığınızda, araç projede iki yeni dosya oluşturur. İlk dosya bir uzantıya sahiptir `.svc` ve WCF çalışma zamanına veri hizmetini nasıl örneklendirilecek. Aşağıda, [hızlı](quickstart-wcf-data-services.md)başlangıcı tamamladığınızda oluşturulan Northwind örnek veri hizmeti için bu dosyaya bir örnek verilmiştir:

```aspx-csharp
<%@ ServiceHost Language="C#"
    Factory="System.Data.Services.DataServiceHostFactory,
            System.Data.Services, Version=4.0.0.0,
            Culture=neutral, PublicKeyToken=b77a5c561934e089"
    Service="NorthwindService.Northwind" %>
```

 Bu yönerge, uygulamanın sınıfını kullanarak adlandırılmış veri hizmeti sınıfı için hizmet ana bilgisayarı oluşturmasını söyler <xref:System.Data.Services.DataServiceHostFactory> .

 Dosya için arka plan kod sayfası, `.svc` Northwind örnek veri hizmeti için aşağıdaki şekilde tanımlanan veri hizmeti 'nin uygulanması olan sınıfı içerir:

 [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
 [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

 Bir veri hizmeti bir WCF hizmeti gibi davrandığı için, veri hizmeti ASP.NET ile tümleşir ve WCF Web programlama modelini izler. Daha fazla bilgi için bkz. [WCF Hizmetleri ve ASP.net](../../wcf/feature-details/wcf-services-and-aspnet.md) ve [WCF Web http programlama modeli](../../wcf/feature-details/wcf-web-http-programming-model.md).

## <a name="self-hosted-wcf-services"></a>WCF hizmetlerini Self-Hosted

 Bir WCF uygulamasını içerdiğinden WCF Veri Hizmetleri, bir WCF hizmeti olarak veri hizmetini kendi kendine barındırmayı destekler. Bir hizmet, konsol uygulaması gibi herhangi bir .NET Framework uygulamasında şirket içinde barınabilir. <xref:System.Data.Services.DataServiceHost>Öğesinden devralan sınıf, <xref:System.ServiceModel.Web.WebServiceHost> belirli bir adreste veri hizmetinin örneğini oluşturmak için kullanılır.

 Self barındırma, hizmeti dağıtmayı ve sorunlarını gidermeyi kolaylaştıran geliştirme ve test için kullanılabilir. Ancak, bu tür bir barındırma, ASP.NET tarafından veya Internet Information Services (IIS) tarafından sunulan gelişmiş barındırma ve yönetim özelliklerini sağlamaz. Daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](../../wcf/feature-details/hosting-in-a-managed-application.md).

## <a name="defining-a-custom-data-service-host"></a>Özel veri hizmeti Konağı tanımlama

 WCF ana bilgisayar uygulamasının çok kısıtlayıcı olduğu durumlarda, bir veri hizmeti için özel bir ana bilgisayar da tanımlayabilirsiniz. Arabirim uygulayan herhangi <xref:System.Data.Services.IDataServiceHost> bir sınıf, bir veri hizmeti için ağ ana bilgisayarı olarak kullanılabilir. Özel bir ana bilgisayar arabirimi uygulamalıdır <xref:System.Data.Services.IDataServiceHost> ve veri hizmeti konağının aşağıdaki temel sorumluluklarını işleyebilmelidir:

- Hizmet kök yolu ile veri hizmeti sağlayın.

- İstek ve yanıt üst bilgileri bilgilerini uygun <xref:System.Data.Services.IDataServiceHost> üye uygulamasına işleyin.

- Veri hizmeti tarafından oluşturulan özel durumları işleyin.

- Sorgu dizesindeki parametreleri doğrulayın.

## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [Verilerinizi Hizmet Olarak Kullanıma Sunma](exposing-your-data-as-a-service-wcf-data-services.md)
- [Veri Hizmeti Yapılandırma](configuring-the-data-service-wcf-data-services.md)
