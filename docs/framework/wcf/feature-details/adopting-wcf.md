---
title: "Windows Communication Foundation'ı Benimseme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e27ee5f2e1b2ad042fd8c0104e89b99eb5e4bc96
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation'ı Benimseme
Kullanmayı tercih edebileceğiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ASP.NET kullanılarak geliştirilmiş uygulamalara sürdürmek devam ederken yeni geliştirme. Çünkü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] olan herhangi bir senaryoda .NET Framework ile oluşturulan uygulamalar ile iletişimi kolaylaştırmanın için en uygun seçenek olarak kullanılması, bu çok çeşitli şekilde yazılım iletişim sorunları çözmek için standart bir aracı olarak hizmet verebilir ASP.NET yapılamıyor.  
  
 Yeni [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar mevcut ASP.NET Web Hizmetleri gibi aynı makinelerde dağıtılabilir. Mevcut ASP.NET Web Hizmetleri .NET Framework sürüm 2.0 önce bir sürümünü kullanmanız sonra ASP.NET IIS Kayıt Aracı'nın yeni, IIS uygulamaları için .NET Framework 2.0 seçmeli olarak dağıtmak için kullanabileceğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalardır barındırılıyor. Bu aracı adresinde belgelenen [ASP.NET IIS Kayıt Aracı (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), ve bir kullanıcı arabirimi yerleşik IIS 6.0 yönetim konsoluna sahip.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ekleyerek mevcut ASP.NET Web Hizmetleri için yeni özellikler eklemek için kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri IIS'ndaki mevcut ASP.NET Web hizmeti uygulama ASP.NET uyumluluk modunda çalışacak şekilde yapılandırılmış. ASP.NET uyumluluğu modu, yeni kodu nedeniyle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri erişebilir ve önceden var olan ASP.NET kodu olarak aynı uygulama durum bilgilerini kullanarak güncelleştirme <xref:System.Web.HttpContext> sınıfı. Uygulamaları, aynı sınıf kitaplıkları da paylaşabilirsiniz.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]istemciler, ASP.NET Web hizmetlerini kullanabilir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ile yapılandırılan hizmetler <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web hizmeti istemciler tarafından kullanılabilir. ASP.NET Web Hizmetleri ile birlikte bulunabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamaları ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bile mevcut ASP.NET Web hizmetlerini özellikleri eklemek için kullanılabilir. Tüm bu şekilde, verilen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET Web Hizmetleri birlikte kullanılabilir, ASP.NET Web hizmetlerini geçirmek istediğiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca tarafından sağlanan özellikleri gerekiyorsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve ASP.NET Web Hizmetleri.  
  
 Gerekli olduğu bile bazı durumlarda, bir teknoloji geçirme koddan diğerine nadiren doğru yaklaşım olduğunu dikkatlice düşünün. Yeni teknoloji benimsenmesi nedeni önceki teknolojisiyle karşılanamıyor yeni gereksinimlerini karşılamak için ve bu durumda, yapmak için doğru olanı yeni Genişletilmiş gereksinimleri karşılaması için yeni bir çözüm tasarımı için. Bu sistem tasarlandığından beri varolan sistem deneyiminizi ve wisdom yeni tasarım avantajları elde edilen. Yeni Tasarım, yeni bir platformda eski tasarım yeniden oluşturma yerine yeni teknolojilerden tam özelliklerini de kullanabilirsiniz. Prototipi oluşturulurken anahtar öğeleri yeni tasarım, sonra bu kodu yeniden kullanma yeni bir içinde mevcut sisteminden daha kolay olur.  
  
 Burada ASP.NET Web sunucusundan taşıma hizmetleri için bazı durumlar için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doğru çözümü, aşağıdaki bölümde, nasıl devam etmek bazı yönergeler sağlanmaktadır. Öneri Hizmetleri'ni geçirmek nasıl ve istemcileri geçirmek nasıl yoktur.  
  
 Mevcut ASP.NET Web hizmetlerini WCF'ye taşıma konusunda tam bir çözümleme için lütfen bkz [ASP.NET Web Hizmetleri ve Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). Bu bölümde meta verilerden uyumlu bir WCF hizmeti, ASP.NET Web hizmeti uygulama ve ASP.NET Web hizmeti ve istemci kodunu taşıma anlatılmaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: meta verileri alma ve uyumlu bir hizmet ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Nasıl yapılır: ASP.NET Web hizmeti kodunu Windows Communication Foundation'a taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Nasıl yapılır: ASP.NET Web hizmeti istemci kodunu Windows Communication Foundation'a taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
