---
title: Arabirim Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 06b2e0d281314f3bd6346a7dbbd8bb56928fe58b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709302"
---
# <a name="interface-design"></a>Arabirim Tasarımı
Çoğu API 'Ler sınıflar ve yapılar kullanılarak en iyi modellense de, arabirimlerin daha uygun veya tek seçenek olduğu durumlar vardır.  
  
 CLR birden çok devralmayı desteklemez (yani, CLR sınıfları birden fazla taban sınıftan devralamaz), ancak türlerin bir temel sınıftan devralmaya ek olarak bir veya daha fazla arabirim uygulamasına izin verir. Bu nedenle, arabirimler genellikle birden çok devralmanın etkisini elde etmek için kullanılır. Örneğin <xref:System.IDisposable>, türlerin katılmak istedikleri diğer devralma hiyerarşisinden bağımsız olarak elden atımı desteklemeye izin veren bir arabirimdir.  
  
 Bir arabirimin tanımlanmasıyla ilgili diğer durum, bazı değer türleri dahil olmak üzere çeşitli türlerde desteklenebilir ortak bir arabirim oluşturmaktır. Değer türleri <xref:System.ValueType>dışındaki türlerden devralınabilir, ancak arabirimler uygulayabilir, bu nedenle bir arabirim kullanmak ortak bir temel tür sağlamak için tek seçenektir.  
  
 **✓ DO** değer türleri içeren bir dizi türleri tarafından desteklenen bazı ortak API gerekiyorsa bir arabirim tanımlayın.  
  
 **✓ CONSIDER** önceden başka bazı türünden devralan türleri işlevselliği desteklemek gereksinim duyarsanız bir arabirim tanımlama.  
  
 **X AVOID** işaret arabirimleri (hiçbir üye arabirimleriyle) kullanarak.  
  
 Bir sınıfı belirli bir özelliğe (işaret) sahip olacak şekilde işaretlemeniz gerekiyorsa, genel olarak, bir arabirim yerine özel bir öznitelik kullanın.  
  
 **✓ DO** bir arabirim uygulaması en az bir türü sağlar.  
  
 Bunu yapmak, arabirimin tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IList%601> arabiriminin bir uygulamasıdır.  
  
 **✓ DO** tanımladığınız her bir arabirime tüketir en az bir API sağlar (bir parametre veya bir özellik arabirimi alma yöntemi yazılan arabirimi olarak).  
  
 Bunu yapmak, arabirim tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimini tüketir.  
  
 **X DO NOT** önceden sevk edilmiş bir arabirim üye ekleyin.  
  
 Bunun yapılması, arabirimin uygulamalarını bozar. Sürüm oluşturma sorunlarından kaçınmak için yeni bir arabirim oluşturmanız gerekir.  
  
 Bu kılavuzlar bölümünde açıklanan durumlar haricinde, genel olarak, yönetilen kod yeniden kullanılabilir kitaplıklarını tasarlarken arabirimler yerine sınıfları seçin.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
