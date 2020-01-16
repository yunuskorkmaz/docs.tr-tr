---
title: Windows Communication Foundation'ı Benimseme
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 53f51c6a93d4768d3aa158d44cb7d20f945393f5
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964253"
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation'ı Benimseme

Yeni geliştirme için Windows Communication Foundation (WCF) kullanmayı seçebilirsiniz, ancak ASP.NET kullanarak geliştirilen mevcut uygulamaları sürdürmeye devam edebilirsiniz. WCF 'nin herhangi bir senaryoda .NET Framework ile oluşturulmuş uygulamalarla iletişimi kolaylaştırmak için en uygun seçim olması amaçlandığından, çok çeşitli yazılım iletişim sorunlarını ASP.NET bir şekilde çözmek için standart bir araç işlevi görebilir. edemez.

Yeni WCF uygulamaları, var olan ASP.NET Web hizmetleriyle aynı makinelere dağıtılabilir. Mevcut ASP.NET Web Hizmetleri sürüm 2,0 ' den önceki bir .NET Framework sürümünü kullanıyorsa, yeni WCF uygulamalarının barındırıldığı IIS uygulamalarına .NET Framework 2,0 ' i seçmeli olarak dağıtmak için ASP.NET IIS kayıt aracı 'nı kullanabilirsiniz. Bu araç [ASP.NET IIS Kayıt Aracı (Aspnet_regiis. exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/k6h9cz8h(v=vs.90))adresinde BELGELENMIŞTIR ve IIS 6,0 yönetim konsoluna yerleşik bir kullanıcı arabirimine sahiptir.

WCF, ASP.NET uyumluluk modunda çalışmak üzere yapılandırılmış WCF hizmetlerini IIS 'de var olan ASP.NET Web hizmeti uygulamalarına ekleyerek mevcut ASP.NET Web hizmetlerine yeni özellikler eklemek için kullanılabilir. ASP.NET uyumluluk modu nedeniyle, yeni WCF hizmetlerinin kodu, <xref:System.Web.HttpContext> sınıfını kullanarak, önceden var olan ASP.NET kodu ile aynı uygulama durumu bilgilerine erişebilir ve güncelleştirebilir. Uygulamalar aynı sınıf kitaplıklarını da paylaşabilir.

WCF istemcileri, ASP.NET Web Hizmetleri 'ni kullanabilir. <xref:System.ServiceModel.BasicHttpBinding> ile yapılandırılan WCF Hizmetleri, ASP.NET Web hizmeti istemcileri tarafından kullanılabilir. ASP.NET Web Hizmetleri WCF uygulamalarıyla birlikte bulunabilir ve WCF, var olan ASP.NET Web hizmetlerine özellikler eklemek için bile kullanılabilir. WCF ve ASP.NET Web hizmetlerinin birlikte kullanılabileceği tüm bu yollar verildiğinde, ASP.NET Web Hizmetleri 'ni yalnızca WCF tarafından sağlanan ve ASP.NET Web Hizmetleri olmayan özelliklere ihtiyacınız varsa WCF 'ye geçirmek isteyebilirsiniz.

Gerekli olduğu durumlarda bile, kodun bir teknolojiden diğerine geçirilmesi nadiren doğru yaklaşımda olur. Yeni teknolojinin benimseme nedeni, önceki teknolojiyle karşılanmayacak yeni gereksinimleri karşılamadır ve bu durumda, doğru olan şey, yeni bir çözüm oluştururken yeni bir çözüm tasarlayamalıdır. Mevcut sistemle ve bu sistem tasarlanmasından bu yana elde edilen wısystem ile deneyiminizden yeni tasarım avantajları. Yeni tasarım, yeni teknolojiden eski tasarımın yerine yeni teknolojilerin tam yeteneklerini de kullanabilir. Yeni tasarımın anahtar öğelerinin prototipi oluşturulduktan sonra, yeni bir sistemdeki kodu yeniden kullanmak daha kolay hale gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Meta Verileri Alma ve Uyumlu Bir Hizmet Ekleme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
