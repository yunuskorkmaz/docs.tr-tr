---
title: Ortak Dil Çalışma Zamanındaki Derlemeler
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b27a8d89b0345082b8cf06c3eb141e73e2bf0faf
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567366"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Ortak Dil Çalışma Zamanındaki Derlemeler
.NET Framework uygulamalarının yapı taşları olan derlemeler dağıtım, sürüm denetimi, yeniden kullanma, aktivasyon kapsamı ve güvenlik izinlerinin de temel birimlerini oluşturur. Bir derleme, birlikte çalışacak ve mantıksal bir işlevsellik birimi oluşturacak biçimde oluşturulan bir tür ve kaynakların bir derlemesidir. Bir derleme, ortak dil çalışma zamanına tür uygulamalarına dikkat etmesi için gerekli bilgileri sunar. Çalışma zamanı için, bir derleme bağlamı dışında bir tür yoktur.  
  
 Bir derleme aşağıdaki işlevleri gerçekleştirir:  
  
- Ortak dil çalışma zamanının yürüttüğü kodu içerir. Bir taşınabilir yürütülebilir (PE) dosyadaki Microsoft ara dil (MSIL) kodu, kendiyle ilişkili herhangi bir derleme bildirimine sahip değilse yürütülmez. Her bir derlemenin yalnızca bir giriş noktasının olduğunu unutmayın (yani, `DllMain`, `WinMain` veya `Main`).  
  
- Bu bir güvenlik sınırı oluşturur. Bir derleme, izinlerin istendiği ve verildiği birimdir. Derlemeler için uygulanan güvenlik sınırları hakkında daha fazla bilgi için bkz. [bütünleştirilmiş kod güvenliği konuları](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
- Bir tür sınır oluşturur. Her tipin kimliği, içinde bulunduğu derlemenin adını içerir. Bir derlemenin kapsamına yüklenen ve `MyType` olarak adlandırılan bir tür, başka bir derlemenin kapsamına yüklenen ve `MyType` olarak adlandırılan türle aynı değildir.  
  
- Bir başvuru kapsam sınırı oluşturur. Derlemenin bildirimi, türleri çözümlemek ve kaynak isteklerini karşılamak için derleme metaverileri içerir. Derlemenin dışından sunulan tür ve kaynakları belirtir. Bildirim ayrıca bağlı olduğu diğer derlemeleri listeler.  
  
- Bir sürüm sınırı oluşturur. Derleme, ortak dil çalışma zamanının en küçük sürümlenebilir birimidir; aynı derleme içerisindeki bütün tür ve kaynaklar bir birim olarak sürümlendirilir. Derlemenin bildirimi, herhangi bir bağımsız derleme için belirttiğiniz sürüm bağımlılıklarını açıklar. Sürüm oluşturma hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md).  
  
- Bir dağıtım birimi oluşturur. Bir uygulama başlatıldığında, sadece uygulamanın başlangıçta çağırdığı derlemeler mevcut olmalıdır. Yerelleştirme kaynakları veya yardımcı sınıflar içeren derlemeler gibi diğer derlemeler geri alınabilir veya talep edilebilir. Bu, uygulamanın ilk indirildiğinde basit ve ince olmasına olanak sağlar. Derlemeleri dağıtma hakkında daha fazla bilgi için bkz. [uygulamaları dağıtma](../../../docs/framework/deployment/index.md).  
  
- Bu, yan yana yürütmenin desteklendiği bir birimdir. Bir derlemenin birden çok sürümünü çalıştırma hakkında daha fazla bilgi için bkz. [derlemeler ve yan yana yürütme](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Derlemeler statik veya dinamik olabilir. Statik derlemeler .NET Framework türlerinin (arabirimler ve sınıflar) yanı sıra, derlemeler için kaynaklar (bitmap'ler, JPEG dosyaları, kaynak dosyaları, vb.) içerebilir. Statik derlemeler, disk üzerinde taşınabilir yürütülebilir (PE) dosyalarda saklanır. .NET Framework kullanarak doğrudan bellekten çalıştırılan ve yürütülmeden önce diske kaydedilmesi gerekmeyen dinamik derlemeler de oluşturabilirsiniz. Yürütüldükten sonra dinamik derlemeleri diske kaydedebilirsiniz.  
  
 Derleme oluşturmak için birçok yol vardır. Geçmişte. dll veya. exe dosyaları oluşturmak için kullandığınız Visual Studio gibi geliştirme araçlarını kullanabilirsiniz. Diğer geliştirme ortamlarında oluşturulan modüllerle derlemeler oluşturmak için Windows SDK sunulan araçları kullanabilirsiniz. Dinamik derlemeler oluşturmak için gibi ortak dil çalışma zamanı API 'lerini <xref:System.Reflection.Emit?displayProperty=nameWithType>de kullanabilirsiniz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Bütünleştirilmiş Kod İçerikleri](../../../docs/framework/app-domains/assembly-contents.md)|Bir derlemeyi oluşturan öğeleri açıklar.|  
|[Bütünleştirilmiş Kod Bildirimi](../../../docs/framework/app-domains/assembly-manifest.md)|Derleme bildirimindeki verileri ve derlemede nasıl depolandığını açıklar.|  
|[Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)|Genel derleme önbelleğini ve derlemelerle birlikte nasıl kullanıldığını açıklar.|  
|[Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/strong-named-assemblies.md)|Tanımlayıcı adlı derlemelerin özelliklerini açıklar.|  
|[Bütünleştirilmiş Kod Güvenliği Konuları](../../../docs/framework/app-domains/assembly-security-considerations.md)|Derlemelerde güvenliğin nasıl kullanıldığını açıklar.|  
|[Bütünleştirilmiş Kod Sürümü Oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)|.NET Framework sürüm oluşturma ilkesine genel bir bakış sunar.|  
|[Bütünleştirilmiş Kod Yerleştirme](../../../docs/framework/app-domains/assembly-placement.md)|Derlemeleri nerede konumlandıracağınızı açıklar.|  
|[Bütünleştirilmiş Kodlar ve Yan Yana Yürütme](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Çalışma zamanının veya bir derlemenin birden çok sürümünü aynı anda kullanmaya genel bir bakış sunar.|  
|[Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)|Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemelerin nasıl oluşturulduğunu açıklar.|  
|[Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|.NET Framework'ün çalışma zamanında derleme başvurularını nasıl çözümlediğini açıklar.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
