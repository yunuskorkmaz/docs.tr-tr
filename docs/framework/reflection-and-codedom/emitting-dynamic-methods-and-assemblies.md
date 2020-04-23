---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180536"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Dinamik Yöntemleri ve Derlemeleri Yayma

Bu bölümde, bir derleyicinin veya aracın, <xref:System.Reflection.Emit> çalışma zamanında meta verileri ve Microsoft ara dili 'NI (MSIL) yayabilmesini ve isteğe bağlı olarak diskte taşınabilir bir ÇALıŞTıRıLABILIR (PE) dosyası oluşturmasını sağlayan ad alanındaki yönetilen türler açıklanmıştır. Komut dosyası motorları ve derleyiciler, bu ad alanının birincil kullanıcılardır. Bu bölümde, <xref:System.Reflection.Emit> ad alanı tarafından sunulan işlevselliğe yansıma yayma denir.  
  
Yansıma yayma aşağıdaki özellikleri sağlar:  
  
- Çalışma zamanında, <xref:System.Reflection.Emit.DynamicMethod> sınıfını kullanarak hafif Global Yöntemler tanımlayın ve temsilcileri kullanarak yürütün.  
  
- Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırın ve/veya diske kaydedin.  
  
- Çalışma zamanında derlemeleri tanımlayın, çalıştırın ve ardından bunları kaldırın ve çöp toplamanın kaynaklarını geri kazanmak için izin verin.  
  
- Çalışma zamanında yeni derlemelerde modüller tanımlayın ve ardından bunları diske kaydedip/veya diske kaydedin.  
  
- Çalışma zamanında modüllerde türler tanımlayın, bu türlerin örneklerini oluşturun ve yöntemlerini çağırın.  
  
- Hata ayıklayıcıları ve kod profil oluşturucular gibi araçlar tarafından kullanılabilen tanımlı modüller için sembolik bilgiler tanımlayın.  
  
<xref:System.Reflection.Emit> Ad alanındaki yönetilen türlerin yanı sıra, [meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır. Yönetilen yansıma yayma, daha güçlü anlamsal hata denetimi ve meta verilerin yönetilmeyen bir soyutlama düzeyini yönetilmeyen meta veri arabirimlerine göre sağlar.  
  
Meta veriler ve MSIL ile çalışmaya yönelik başka bir faydalı kaynak, yaygın olarak kullanılan dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CıL yönerge kümesi". Belgeler, [ecma Web sitesinde](https://www.ecma-international.org/publications/standards/Ecma-335.htm)çevrimiçi olarak sunulmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde
  
[Yansıma Yaymadaki güvenlik sorunları](security-issues-in-reflection-emit.md)  
Yansıma yayma kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik konularını açıklar.  

[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) Basit bir dinamik yöntemin ve bir sınıfın örneğine bağlantılı dinamik yöntemin nasıl yürütüleceğini gösterir.

[Nasıl yapılır: yansıma yayma ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md) İki tür parametresiyle basit bir genel türün nasıl oluşturulduğunu, tür parametrelerine sınıf, arabirim ve özel kısıtlamaları uygulamayı ve sınıfın tür parametrelerini parametre türleri ve dönüş türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir.

[Nasıl yapılır: yansıma yayma ile genel bir yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md) Basit bir genel yöntemin nasıl oluşturulacağını, yayalınacağını ve çağıralınacağını gösterir.

[Dinamik tür oluşturma Için toplanabilir derlemeler](collectible-assemblies.md) , Oluşturuldukları uygulama etki alanını kaldırmadan kaldırılabilen dinamik derlemeler olan toplanabilir derlemeleri tanıtır.
  
## <a name="reference"></a>Başvuru  

<xref:System.Reflection.Emit.OpCodes>  
Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL Yönerge kodlarını kataloglandırır.  
  
<xref:System.Reflection.Emit>  
Dinamik yöntemleri, derlemeleri ve türleri yayma için kullanılan yönetilen sınıfları içerir.  
  
<xref:System.Type>  
Yönetilen yansıma <xref:System.Type> ve yansıma yayma türlerini temsil eden ve bu teknolojilerin kullanımına yönelik anahtar olan sınıfını açıklar.  
  
<xref:System.Reflection>  
Meta verileri ve yönetilen kodu araştırmak için kullanılan yönetilen sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  

[Yansıma](reflection.md)  
Meta verilerin ve yönetilen kodun nasıl araştırılacağını açıklar.  
  
[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)  
.NET uygulamalarında derlemelere genel bakış sağlar.
