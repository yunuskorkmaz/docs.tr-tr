---
title: Uygulama Etki Alanları ve Derlemelerle Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 3f66eacaf30f8001cdbf3a486e5ce1c878712e2f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644280"
---
# <a name="programming-with-application-domains-and-assemblies"></a>Uygulama Etki Alanları ve Derlemelerle Programlama

Microsoft Internet Explorer, ASP.NET ve Windows kabuğu gibi konaklar, ortak dil çalışma zamanını bir işleme yükler, bu işlemde bir [uygulama etki alanı](application-domains.md) oluşturur ve ardından .NET Framework bir uygulama çalıştırırken bu uygulama etki alanında Kullanıcı kodunu yükler ve yürütür. Çoğu durumda, çalışma zamanı ana bilgisayarı bu görevleri gerçekleştirdiğinden, uygulama etki alanları oluşturma ve bunlara derleme yükleme konusunda endişelenmeniz gerekmez.  
  
Bununla birlikte, ortak dil çalışma zamanını barındıracak bir uygulama oluşturuyorsanız, programlı olarak kaldırmak istediğiniz araçları veya kodu oluşturun ya da bir yandan kaldırılabileceğiniz ve yeniden yüklenebilir olan takılabilir bileşenler oluşturun, kendi uygulama etki alanlarınızı oluşturursunuz. Çalışma zamanı ana bilgisayarı oluşturmasanız bile, bu bölümde bu uygulama etki alanlarında yüklü uygulama etki alanları ve Derlemeleriyle çalışma hakkında önemli bilgiler verilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

[Uygulama Etki Alanları ve Derlemeler Nasıl Yapılır Konuları](application-domains-and-assemblies-how-to-topics.md)  
Uygulama etki alanları ve Derlemeleriyle programlama için kavramsal belgelerde bulunan tüm nasıl yapılır konularına bağlantılar sağlar.  
  
[Uygulama Etki Alanlarını Kullanma](use.md)  
Uygulama etki alanları oluşturma, yapılandırma ve kullanma örnekleri sunar.  
  
[Derlemelerle Programlama](../../standard/assembly/index.md)  
Derlemelerde nasıl öznitelik oluşturacağınızı, işaretleyeceğinizi ve ayarlayacağınızı açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

[Dinamik Yöntemleri ve Derlemeleri Yayma](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
Dinamik derlemelerin nasıl oluşturulduğunu açıklar.  
  
[.NET’te bütünleştirilmiş kodlar](../../standard/assembly/index.md)  
Derlemeler üzerine kavramsal bir genel bakış sağlar.  
  
[Uygulama Etki Alanları](application-domains.md)  
Uygulama etki alanları üzerine kavramsal bir genel bakış sağlar.  
  
[Yansımaya genel bakış](../reflection-and-codedom/reflection.md)  
Bir derleme hakkında bilgi almak için **yansıma** sınıfının nasıl kullanılacağını açıklar.
