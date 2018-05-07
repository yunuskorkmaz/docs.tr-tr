---
title: Windows Communication Foundation'ı Benimseme
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: bcd6543e6cd47dc723b308acebec6f492fa14fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation'ı Benimseme
ASP.NET kullanılarak geliştirilmiş uygulamalara sürdürmek devam ederken yeni geliştirme projeleri için Windows Communication Foundation (WCF) kullanmayı seçebilirsiniz. WCF herhangi bir senaryoda .NET Framework ile oluşturulan uygulamalar ile iletişimi kolaylaştırmanın için en uygun seçenek amaçlandığından, çok çeşitli şekilde yazılım iletişim sorunları çözmek için standart bir araç olarak ASP.NET görebilir uygulanamaz.  
  
 Yeni WCF uygulamaları mevcut ASP.NET Web Hizmetleri ile aynı makinede dağıtılabilir. Mevcut ASP.NET Web Hizmetleri, .NET Framework sürüm 2.0 önce bir sürümünü kullanıyorsanız, seçmeli olarak .NET Framework 2.0 yeni WCF uygulamaları barındırılacak şekilde olduğu IIS uygulama dağıtmak için ASP.NET IIS Kayıt aracını kullanabilirsiniz. Bu aracı adresinde belgelenen [ASP.NET IIS Kayıt Aracı (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), ve bir kullanıcı arabirimi yerleşik IIS 6.0 yönetim konsoluna sahip.  
  
 WCF IIS'ndaki mevcut ASP.NET Web hizmeti uygulama ASP.NET uyumluluk modunda çalışacak şekilde yapılandırılmış WCF hizmetleri ekleyerek mevcut ASP.NET Web Hizmetleri için yeni özellikler eklemek için kullanılabilir. ASP.NET uyumluluğu modunu nedeniyle yeni WCF hizmetleri için kod erişebilir ve önceden var olan ASP.NET kodu olarak aynı uygulama durum bilgilerini kullanarak güncelleştirme <xref:System.Web.HttpContext> sınıfı. Uygulamaları, aynı sınıf kitaplıkları da paylaşabilirsiniz.  
  
 WCF istemcileri, ASP.NET Web hizmetlerini kullanabilirsiniz. İle yapılandırılmış WCF hizmetleri <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web hizmeti istemciler tarafından kullanılabilir. ASP.NET Web Hizmetleri ile WCF uygulamaları birlikte bulunabilir ve WCF bile mevcut ASP.NET Web hizmetlerini özellikleri eklemek için kullanılabilir. Bu şekilde, WCF ve ASP.NET Web Hizmetleri birlikte kullanılabilir mi tümünün verilen, yalnızca WCF ve ASP.NET Web Hizmetleri tarafından sağlanan özellikleri gerekiyorsa ASP.NET Web hizmetlerini WCF'ye taşıma isteyebilirsiniz.  
  
 Gerekli olduğu bile bazı durumlarda, bir teknoloji geçirme koddan diğerine nadiren doğru yaklaşım olduğunu dikkatlice düşünün. Yeni teknoloji benimsenmesi nedeni önceki teknolojisiyle karşılanamıyor yeni gereksinimlerini karşılamak için ve bu durumda, yapmak için doğru olanı yeni Genişletilmiş gereksinimleri karşılaması için yeni bir çözüm tasarımı için. Bu sistem tasarlandığından beri varolan sistem deneyiminizi ve wisdom yeni tasarım avantajları elde edilen. Yeni Tasarım, yeni bir platformda eski tasarım yeniden oluşturma yerine yeni teknolojilerden tam özelliklerini de kullanabilirsiniz. Prototipi oluşturulurken anahtar öğeleri yeni tasarım, sonra bu kodu yeniden kullanma yeni bir içinde mevcut sisteminden daha kolay olur.  
  
 ASP.NET Web hizmetlerini WCF'ye taşıma burada birkaç durumda olduğu için doğru çözüm, aşağıdaki bölümde nasıl devam etmek bazı yönergeler sağlanmaktadır. Öneri Hizmetleri'ni geçirmek nasıl ve istemcileri geçirmek nasıl yoktur.  
  
 Mevcut ASP.NET Web hizmetlerini WCF'ye taşıma konusunda tam bir çözümleme için lütfen bkz [ASP.NET Web Hizmetleri ve Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). Bu bölümde meta verilerden uyumlu bir WCF hizmeti, ASP.NET Web hizmeti uygulama ve ASP.NET Web hizmeti ve istemci kodunu WCF'ye taşıma anlatılmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Nasıl yapılır: ASP.NET Web Hizmeti Kodunu Windows Communication Foundation'a Taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Nasıl yapılır: ASP.NET Web Hizmeti İstemci Kodunu Windows Communication Foundation'a Taşıma](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
