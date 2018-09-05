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
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562378"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Dinamik Yöntemleri ve Derlemeleri Yayma
Bu bölümde bir yönetilen türleri açıklar <xref:System.Reflection.Emit> izin derleyici veya aracının meta verileri ve Microsoft Ara dilini (MSIL) çalışma zamanında ve isteğe bağlı olarak göstermek için bir ad alanı diskte taşınabilir yürütülebilir (PE) dosya oluşturur. Komut dosyası motorları ve derleyiciler bu ad alanının birincil kullanıcıları olan. Bu bölümde, işlevi tarafından sağlanan <xref:System.Reflection.Emit> ad alanı yansıma yayma adlandırılır.  
  
 Yansıma yayma aşağıdaki özellikleri sağlar:  
  
-   Basit genel definovat çalıştırmada kullandığınızdan <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve bunları yürütmek temsilcileri kullanma.  
  
-   Çalışma zamanında derlemeleri tanımlayın ve ardından bunları çalıştırmak ve/veya diske kaydedin.  
  
-   Çalışma zamanında derlemeleri tanımlamak, bunları, bunları kaldırma ve kendi kaynaklarınızı geri kazanmanız çöp toplamaya olanak tanımak.  
  
-   Modüller yeni derlemelerde çalışma zamanında tanımlayın ve ardından çalıştırın ve/veya diske kaydedin.  
  
-   Çalışma zamanında modüllerde türlerini tanımlayın, bu türlerin örneklerini oluşturmak ve kendi yöntemlerini çağırmak.  
  
-   Hata ayıklayıcıları ve kod profil oluşturucuları gibi araçlar tarafından kullanılan tanımlanmış modüller için simgesel bilgiler tanımlayın.  
  
 Yönetilen türleri yanı sıra <xref:System.Reflection.Emit> ad alanı, açıklanan yönetilmeyen meta veri arabirimleri vardır [meta veri arabirimleri](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) başvuru belgeleri. Yönetilen yansıma yayma daha güçlü anlamsal hata denetimi ve daha yüksek düzeyde soyutlama meta verilerin daha yönetilmeyen meta veri arabirimleri sağlar.  
  
 MSIL ve meta verileri ile çalışmak için yararlı başka bir kaynak ortak dil altyapısı (CLI), "özellikle Bölüm II: meta veri tanımı ve semantiği" ve "Bölüm III: CIL yönerge kümesi" belgelerdir. Belgeler hakkında çevrimiçi kullanılabilir [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) ve [Ecma Web sitesi](https://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>Bu Bölümde
  
[Yaymadaki güvenlik sorunları yansıma](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
Güvenlik yaymadaki yansıma kullanarak dinamik derlemeler oluşturma işlemiyle ilgili sorunları açıklar.  

[Nasıl yapılır: dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md)   
Basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı olarak dinamik bir yöntem yürütme işlemi gösterilmektedir.

[Nasıl yapılır: yansıma ile genel tür tanımlama yayma](how-to-define-a-generic-type-with-reflection-emit.md)   
İki tür parametreleri ile basit bir genel tür oluşturma için tür parametreleri, sınıf, arabirim ve özel kısıtlamalar uygulamak nasıl ve sınıf türü parametreler parametre türleri olarak kullanın ve dönüş türleri üye oluşturma işlemini gösterir.

[Nasıl yapılır: yansıma ile genel yöntem tanımlama yayma](how-to-define-a-generic-method-with-reflection-emit.md)   
Basit bir genel yöntem çağırma oluşturun ve yayma işlemi gösterilmektedir.

[Dinamik tür oluşturma için toplanabilir derlemeler](collectible-assemblies.md)   
Oluşturulmuş olan uygulama etki alanını kaldırmadan kaldırılabilip kaldırılamayacağını dinamik derlemeler toplanabilir derlemeler tanıtır.
  
## <a name="reference"></a>Başvuru  
 <xref:System.Reflection.Emit.OpCodes>  
 Metot gövdeleri oluşturmak için kullanabileceğiniz MSIL yönergesi kodları kataloglar.  
  
 <xref:System.Reflection.Emit>  
 Türleri dinamik yöntemleri ve derlemeleri Yayma almak için kullanılan yönetilen sınıflar içerir.  
  
 <xref:System.Type>  
 Açıklar <xref:System.Type> türleri temsil eden sınıf yönetilen yansıma ve yansıma yayma ve bu teknolojilerin kullanımını anahtarına olduğu.  
  
 <xref:System.Reflection>  
 Meta veriler ve yönetilen kod keşfetmek için kullanılan yönetilen sınıflar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Meta veriler ve yönetilen kod keşfedin açıklanmaktadır.  
  
 [Ortak Dil Çalışma Zamanı Modülündeki Bütünleştirilmiş Kodlar](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Derlemeler .NET uygulamalarında genel bir bakış sağlar.
