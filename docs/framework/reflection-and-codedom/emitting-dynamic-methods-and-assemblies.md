---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
description: Bir derleyicinin veya aracın çalışma zamanında meta verileri ve MSIL kodunu yaymasına izin veren System. Reflection. yayma ad alanını kullanarak dinamik yöntemleri ve derlemeleri yayma.
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 76d2a83943d9df06cc66cf86c6869f18fac2a12c
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475053"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Dinamik Yöntemleri ve Derlemeleri Yayma

Bu bölümde, <xref:System.Reflection.Emit> bir derleyicinin veya aracın, çalışma zamanında meta verileri ve Microsoft ara dili 'ni (MSIL) yayabilmesini ve isteğe bağlı olarak diskte taşınabilir bir çalıştırılabilir (PE) dosyası oluşturmasını sağlayan ad alanındaki yönetilen türler açıklanmıştır. Komut dosyası motorları ve derleyiciler, bu ad alanının birincil kullanıcılardır. Bu bölümde, ad alanı tarafından sunulan işlevselliğe <xref:System.Reflection.Emit> yansıma yayma denir.  
  
Yansıma yayma aşağıdaki özellikleri sağlar:  
  
- Çalışma zamanında, sınıfını kullanarak hafif Global Yöntemler tanımlayın <xref:System.Reflection.Emit.DynamicMethod> ve temsilcileri kullanarak yürütün.  
  
- Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırın ve/veya diske kaydedin.  
  
- Çalışma zamanında derlemeleri tanımlayın, çalıştırın ve ardından bunları kaldırın ve çöp toplamanın kaynaklarını geri kazanmak için izin verin.  
  
- Çalışma zamanında yeni derlemelerde modüller tanımlayın ve ardından bunları diske kaydedip/veya diske kaydedin.  
  
- Çalışma zamanında modüllerde türler tanımlayın, bu türlerin örneklerini oluşturun ve yöntemlerini çağırın.  
  
- Hata ayıklayıcıları ve kod profil oluşturucular gibi araçlar tarafından kullanılabilen tanımlı modüller için sembolik bilgiler tanımlayın.  
  
Ad alanındaki yönetilen türlerin yanı sıra <xref:System.Reflection.Emit> , [meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır. Yönetilen yansıma yayma, daha güçlü anlamsal hata denetimi ve meta verilerin yönetilmeyen bir soyutlama düzeyini yönetilmeyen meta veri arabirimlerine göre sağlar.  
  
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
<xref:System.Type>Yönetilen yansıma ve yansıma yayma türlerini temsil eden ve bu teknolojilerin kullanımına yönelik anahtar olan sınıfını açıklar.  
  
<xref:System.Reflection>  
Meta verileri ve yönetilen kodu araştırmak için kullanılan yönetilen sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  

[Yansıma](reflection.md)  
Meta verilerin ve yönetilen kodun nasıl araştırılacağını açıklar.  
  
[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)  
.NET uygulamalarında derlemelere genel bakış sağlar.
