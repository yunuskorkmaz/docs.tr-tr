---
title: Windows Communication Foundation'ı Benimseme
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 5773d2687eb06cfc562dbe25fa9b94864b1b3a49
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565556"
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation'ı Benimseme

ASP.NET kullanılarak geliştirilen mevcut uygulamaları korumak devam ederken, yeni geliştirme projeleri için Windows Communication Foundation (WCF) kullanmayı da tercih edebilirsiniz. WCF hiçbir senaryoda .NET Framework ile oluşturulan uygulamalar ile iletişimi etkinleştirme için en uygun seçeneği olacak şekilde tasarlandığından, çok çeşitli yazılım bir şekilde iletişim sorunlarını çözmek için standart bir araç ASP.NET görebilir uygulanamaz.

Yeni WCF uygulamaları mevcut ASP.NET Web Hizmetleri olarak aynı makinede dağıtılabilir. Mevcut ASP.NET Web Hizmetleri .NET Framework 2.0 sürümünden önceki bir sürümünü kullanıyorsanız, seçmeli olarak .NET Framework 2.0, barındırılması için yeni WCF uygulamaları olduğu IIS uygulama dağıtmak için ASP.NET IIS Kayıt aracını kullanabilirsiniz. Bu aracı adresinde belgelenen [ASP.NET IIS Kayıt Aracı (Aspnet_regiis.exe)](https://go.microsoft.com/fwlink/?LinkId=94687), ve IIS 6.0 yönetim konsoluna oluşturduğu bir kullanıcı arabirimi.

WCF, IIS mevcut ASP.NET Web hizmeti uygulama için ASP.NET uyumluluk modunda çalışacak şekilde yapılandırılmış WCF hizmetlerini ekleyerek mevcut bir ASP.NET Web Hizmetleri için yeni özellikler eklemek için kullanılabilir. ASP.NET uyumluluk modunun nedeniyle yeni WCF hizmetleri için kod erişebilir ve aynı uygulama durumu bilgileri önceden mevcut olan ASP.NET kodunu kullanarak güncelleştirme <xref:System.Web.HttpContext> sınıfı. Uygulamalar Ayrıca aynı sınıf kitaplıkları paylaşabilirsiniz.

WCF istemcileri, ASP.NET Web hizmetlerini kullanabilirsiniz. İle yapılandırılan WCF hizmetleri <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web hizmeti istemcileri tarafından kullanılabilir. ASP.NET Web Hizmetleri ile WCF uygulamaları birlikte bulunabilir ve WCF bile var olan ASP.NET Web hizmetlerini özellikleri eklemek için kullanılabilir. Tüm yolların, WCF ve ASP.NET Web hizmetlerini birlikte kullanılabilmesi için göz önünde bulundurulduğunda, WCF ve ASP.NET Web Hizmetleri tarafından sağlanan özellikler gerektiriyorsa, ASP.NET Web hizmetlerini WCF'ye taşıma isteyebilirsiniz.

Gerekli olduğu bazı durumlarda bile, bir teknoloji geçirme koddan diğerine nadiren doğru bir yaklaşımdır. Yeni Teknoloji benimseme nedeni önceki teknolojisiyle karşılanamıyor yeni gereksinimlerini karşılamak için ve bu durumda, doğru bir şey yapmak için yeni Genişletilmiş gereksinimlerini karşılaması için yeni bir çözüm tasarlamak için. Bu sistem tasarlandığından beri yeni tasarım avantajları bilgilerini ve mevcut sistem deneyiminizi kavuştu. Yeni tasarım özelliklerinin tamamı yeni platformunda eski tasarım yeniden yerine yeni teknolojileri de kullanabilirsiniz. Prototip oluşturma anahtar yeni tasarım öğeleri sonra kod yeniden kullanımı için yeni bir tane var olan sistemden daha kolay olur.

## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
