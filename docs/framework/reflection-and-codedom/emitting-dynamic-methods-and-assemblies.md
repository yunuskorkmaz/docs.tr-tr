---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 4578b708b10e93a7f5def5b9dc040eeb646bdc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130242"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Dinamik Yöntemleri ve Derlemeleri Yayma

Bu bölümde, bir derleyicinin veya aracın, çalışma zamanında meta verileri ve Microsoft ara dili 'ni (MSIL) yayabilmesini ve isteğe bağlı olarak diskte taşınabilir bir çalıştırılabilir (PE) dosyası oluşturmasını sağlayan <xref:System.Reflection.Emit> ad alanındaki bir yönetilen türler kümesi açıklanmaktadır. Komut dosyası motorları ve derleyiciler, bu ad alanının birincil kullanıcılardır. Bu bölümde, <xref:System.Reflection.Emit> ad alanı tarafından sunulan işlevselliğe yansıma yayma denir.  
  
Yansıma yayma aşağıdaki özellikleri sağlar:  
  
- Çalışma zamanında hafif Global Yöntemler tanımlayın, <xref:System.Reflection.Emit.DynamicMethod> sınıfını kullanarak bunları temsilciler kullanarak yürütün.  
  
- Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırın ve/veya diske kaydedin.  
  
- Çalışma zamanında derlemeleri tanımlayın, çalıştırın ve ardından bunları kaldırın ve çöp toplamanın kaynaklarını geri kazanmak için izin verin.  
  
- Çalışma zamanında yeni derlemelerde modüller tanımlayın ve ardından bunları diske kaydedip/veya diske kaydedin.  
  
- Çalışma zamanında modüllerde türler tanımlayın, bu türlerin örneklerini oluşturun ve yöntemlerini çağırın.  
  
- Hata ayıklayıcıları ve kod profil oluşturucular gibi araçlar tarafından kullanılabilen tanımlı modüller için sembolik bilgiler tanımlayın.  
  
<xref:System.Reflection.Emit> ad alanındaki yönetilen türlere ek olarak, [meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır. Yönetilen yansıma yayma, daha güçlü anlamsal hata denetimi ve meta verilerin yönetilmeyen bir soyutlama düzeyini yönetilmeyen meta veri arabirimlerine göre sağlar.  
  
Meta veriler ve MSIL ile çalışmaya yönelik başka bir faydalı kaynak, yaygın olarak kullanılan dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CıL yönerge kümesi". Belgeler, [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) ve [ecma Web sitesinde](https://go.microsoft.com/fwlink/?LinkId=116487)çevrimiçi olarak sunulmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde
  
[Yansıma Yaymadaki güvenlik sorunları](security-issues-in-reflection-emit.md)  
Yansıma yayma kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik konularını açıklar.  

[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md)   
Basit bir dinamik yöntemin ve bir sınıfın örneğine bağlantılı dinamik yöntemin nasıl yürütüleceğini gösterir.

[Nasıl yapılır: yansıma yayma ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)   
İki tür parametresiyle basit bir genel türün nasıl oluşturulduğunu, tür parametrelerine sınıf, arabirim ve özel kısıtlamaları uygulamayı ve sınıfın tür parametrelerini parametre türleri ve dönüş türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir.

[Nasıl yapılır: yansıma yayma ile genel bir yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md)   
Basit bir genel yöntemin nasıl oluşturulacağını, yayalınacağını ve çağıralınacağını gösterir.

[Dinamik tür oluşturma Için toplanabilir derlemeler](collectible-assemblies.md)   
, Oluşturuldukları uygulama etki alanını kaldırmadan kaldırılabilen dinamik derlemeler olan toplanabilir derlemeleri tanıtır.
  
## <a name="reference"></a>Başvuru  

<xref:System.Reflection.Emit.OpCodes>  
Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL Yönerge kodlarını kataloglandırır.  
  
<xref:System.Reflection.Emit>  
Dinamik yöntemleri, derlemeleri ve türleri yayma için kullanılan yönetilen sınıfları içerir.  
  
<xref:System.Type>  
Yönetilen yansıma ve yansıma yayma türlerini temsil eden ve bu teknolojilerin kullanımına yönelik anahtar olan <xref:System.Type> sınıfını açıklar.  
  
<xref:System.Reflection>  
Meta verileri ve yönetilen kodu araştırmak için kullanılan yönetilen sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  

[Yansıma](reflection.md)  
Meta verilerin ve yönetilen kodun nasıl araştırılacağını açıklar.  
  
[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)  
.NET uygulamalarında derlemelere genel bakış sağlar.
