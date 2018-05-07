---
title: Dinamik Yöntemleri ve Derlemeleri Yayma
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6d5085b846a10fe86a87e19738e1b159e300c5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Dinamik Yöntemleri ve Derlemeleri Yayma
Bu bölümde bir yönetilen türlerinde açıklar <xref:System.Reflection.Emit> derleyici veya meta veri ve Microsoft Ara dili (MSIL çalışma zamanında ve isteğe bağlı olarak) yaymak üzere aracı izin ad alanı oluşturmak disk üzerinde bir taşınabilir yürütülebilir (PE) dosyası. Komut dosyası motorları ve derleyicileri bu ad alanı birincil kullanıcıları olan. Bu bölümde, işlev tarafından sağlanan <xref:System.Reflection.Emit> ad alanı yansıma yayma adlandırılır.  
  
 Yansıma yayma aşağıdaki yetenekleri sağlar:  
  
-   Basit genel yöntemler çalışma tanımlamak, kullanarak istediğiniz zaman <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve bunları yürütmek temsilcileri kullanma.  
  
-   Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırmak ve/veya diske kaydedin.  
  
-   Çalışma zamanında derlemeleri tanımlamak, bunları ve ardından bunları kaldırma çalıştırıp kaynaklarını geri kazanmak atık toplama izin verin.  
  
-   Modülleri çalışma zamanında yeni derlemelerde tanımlayın ve ardından çalıştırın ve/veya diske kaydedin.  
  
-   Modülleri çalışma zamanında türlerini tanımlayın, bu tür örnekleri oluşturmak ve kendi yöntemlerini çağırın.  
  
-   Simgesel hata ayıklayıcıları ve kod profil oluşturucuları gibi araçları tarafından kullanılan tanımlı modülleri bilgilerini tanımlayın.  
  
 Yönetilen türler yanı sıra <xref:System.Reflection.Emit> ad alanı, açıklanan yönetilmeyen meta veri arabirimleri vardır [meta veri arabirimleri](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerini. Yönetilen yansıma yayma daha güçlü anlamsal hata denetimi ve yönetilmeyen meta veri arabirimleri soyutlama meta verilerin daha üst bir düzeyde sağlar.  
  
 MSIL ve meta verileri ile çalışmak için başka bir kullanışlı "özellikle Bölüm II: meta veri tanım ve semantik" ve "Bölüm III: CIL yönerge kümesi" ortak dil altyapısı (CLI) belgeleri kaynaktır. Belge üzerinde çevrimiçidir [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) ve [Ecma Web sitesi](http://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>Bu Bölümde
  
[Güvenlik sorunları yansıma yayma](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
Yansıma kullanarak dinamik derlemeleri oluşturulmasıyla ilgili sorunları yayma güvenlik açıklar.  

[Nasıl yapılır: dinamik yöntemleri çalıştırma ve tanımlayın](how-to-define-and-execute-dynamic-methods.md)   
Nasıl basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı dinamik yöntemi yürütüleceği gösterilmektedir.

[Nasıl yapılır: yansıma ile genel tür tanımlama yayma](how-to-define-a-generic-type-with-reflection-emit.md)   
İki tür parametreleri ile basit bir genel tür oluşturma, tür parametreleri sınıfı, arabirimi ve özel kısıtlamalar uygulamak nasıl ve parametre türleri olarak sınıfının tür parametreleri kullanan ve dönüş türleri memers oluşturulacağını gösterir.

[Nasıl yapılır: yansıma ile genel yöntem tanımlama yayma](how-to-define-a-generic-method-with-reflection-emit.md)   
Oluşturma, yayma ve basit bir genel yöntem çağırma gösterir.

[Dinamik tür oluşturma için collectible derlemeler](collectible-assemblies.md)   
Bunlar oluşturulduğu uygulama etki alanı kaldırılması olmadan kaldırılamıyor dinamik derlemeleri collectible derlemeler tanıtır.
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Emit.OpCodes>  
 Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL yönerge kodları kataloglar.  
  
 <xref:System.Reflection.Emit>  
 Dinamik yöntemleri, derlemeler ve türleri yaymak üzere kullanılan yönetilen sınıflar içerir.  
  
 <xref:System.Type>  
 Açıklar <xref:System.Type> yönetilen yansıma türleri temsil eden sınıf ve yansıma yayma ve bu teknolojiler kullanımını anahtarına olduğu.  
  
 <xref:System.Reflection>  
 Meta veri ve yönetilen kod keşfetmek için kullanılan yönetilen sınıflar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Meta veri ve yönetilen kod keşfetmek açıklanmaktadır.  
  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 .NET uygulamalarında derlemeleri genel bir bakış sağlar.
