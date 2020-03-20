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

Bu bölümde, <xref:System.Reflection.Emit> ad alanında, derleyicinin veya aracın çalışma zamanında meta veri ve Microsoft ara dili (MSIL) yayarlar ve isteğe bağlı olarak diskte taşınabilir bir yürütülebilir (PE) dosya oluşturmasına olanak tanıyan yönetilen türler kümesi açıklanır. Komut dosyası motorları ve derleyiciler bu ad alanının birincil kullanıcılarıdır. Bu bölümde, <xref:System.Reflection.Emit> ad alanı tarafından sağlanan işlevsellik yansıma yayan olarak adlandırılır.  
  
Yansıma yayan aşağıdaki yetenekleri sağlar:  
  
- Sınıfı kullanarak çalışma zamanında hafif <xref:System.Reflection.Emit.DynamicMethod> genel yöntemleri tanımlayın ve bunları temsilciler kullanarak çalıştırın.  
  
- Derlemeleri çalışma zamanında tanımlayın ve çalıştırın ve/veya diske kaydedin.  
  
- Derlemeleri çalışma zamanında tanımlayın, çalıştırın ve sonra boşaltın ve çöp toplamanın kaynaklarını geri almasına izin verin.  
  
- Modülleri çalışma zamanında yeni derlemelerde tanımlayın ve ardından çalıştırın ve/veya diske kaydedin.  
  
- Çalışma zamanında modüllerde türleri tanımlayın, bu tür örnekleri oluşturun ve yöntemlerini çağırın.  
  
- Hata ayıklayıcılar ve kod profilcileri gibi araçlar tarafından kullanılabilecek tanımlanmış modüller için sembolik bilgileri tanımlayın.  
  
Ad alanında yönetilen türlere ek olarak, [Meta veri arabirimleri](../unmanaged-api/metadata/metadata-interfaces.md) başvuru belgelerinde açıklanan yönetilmeyen meta veri arabirimleri vardır. <xref:System.Reflection.Emit> Yönetilen yansıma, daha güçlü anlamsal hata denetimi ve yönetilmeyen meta veri arabirimlerinden daha yüksek bir soyutlama düzeyi sağlar.  
  
Meta veri ve MSIL ile çalışmak için bir diğer yararlı kaynak ortak dil altyapısı (CLI) belgeleri, özellikle "Bölüm II: Meta veri tanımı ve semantik" ve "Bölüm III: CIL Öğretim Kümesi"dir. Dokümantasyon [Ecma Web sitesinde](https://www.ecma-international.org/publications/standards/Ecma-335.htm)nağmeler online olarak mevcuttur.  
  
## <a name="in-this-section"></a>Bu Bölümde
  
[Yansıma yayan güvenlik sorunları](security-issues-in-reflection-emit.md)  
Yansıma yonu kullanarak dinamik derlemeler oluşturmayla ilgili güvenlik sorunlarını açıklar.  

[Nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme](how-to-define-and-execute-dynamic-methods.md) Basit bir dinamik yöntemin ve sınıfın örneğine bağlı dinamik bir yöntemin nasıl yürütüleceklerini gösterir.

[Nasıl yapılır: Yansıma yayıyla genel bir tür tanımla](how-to-define-a-generic-type-with-reflection-emit.md) İki tür parametresi içeren basit bir genel yazının nasıl oluşturulacağı, sınıf, arabirim ve özel kısıtlamaların tür parametrelerine nasıl uygulanacağı ve sınıfın tür parametrelerini parametre türleri ve iade türleri olarak kullanan üyelerin nasıl oluşturulacağı gösterilmektedir.

[Nasıl yapılsın: Yansıma yayan genel bir yöntem tanımlayın](how-to-define-a-generic-method-with-reflection-emit.md) Basit bir genel yöntemin nasıl oluşturulup, yarayıp nasıl başlatılsüreceğini ve çağırılabildiğini gösterir.

[Dinamik tip üretimi için tahsil montajları](collectible-assemblies.md) Oluşturuldukları uygulama etki alanını boşaltmadan boşaltılabilen dinamik derlemeler olan tahsil derlemeleri sunar.
  
## <a name="reference"></a>Başvuru  

<xref:System.Reflection.Emit.OpCodes>  
Yöntem gövdeleri oluşturmak için kullanabileceğiniz MSIL talimat kodlarını kataloglar.  
  
<xref:System.Reflection.Emit>  
Dinamik yöntemler, derlemeler ve türler yontmak için kullanılan yönetilen sınıfları içerir.  
  
<xref:System.Type>  
Yönetilen <xref:System.Type> yansıma ve yansıma yayan türleri temsil eden ve bu teknolojilerin kullanımının anahtarı olan sınıfı açıklar.  
  
<xref:System.Reflection>  
Meta verileri ve yönetilen kodu keşfetmek için kullanılan yönetilen sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  

[Yansıma](reflection.md)  
Meta verilerin ve yönetilen kodun nasıl araştırılabildiğini açıklar.  
  
[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)  
.NET uygulamalarındaki derlemelere genel bir bakış sağlar.
