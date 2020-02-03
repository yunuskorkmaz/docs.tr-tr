---
title: Arabirim Tasarımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 544035180a5004bfe2f4c75c680116e52bf25f98
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744155"
---
# <a name="interface-design"></a>Arabirim Tasarımı
Çoğu API 'Ler sınıflar ve yapılar kullanılarak en iyi modellense de, arabirimlerin daha uygun veya tek seçenek olduğu durumlar vardır.

 CLR birden çok devralmayı desteklemez (yani, CLR sınıfları birden fazla taban sınıftan devralamaz), ancak türlerin bir temel sınıftan devralmaya ek olarak bir veya daha fazla arabirim uygulamasına izin verir. Bu nedenle, arabirimler genellikle birden çok devralmanın etkisini elde etmek için kullanılır. Örneğin <xref:System.IDisposable>, türlerin katılmak istedikleri diğer devralma hiyerarşisinden bağımsız olarak elden atımı desteklemeye izin veren bir arabirimdir.

 Bir arabirimin tanımlanmasıyla ilgili diğer durum, bazı değer türleri dahil olmak üzere çeşitli türlerde desteklenebilir ortak bir arabirim oluşturmaktır. Değer türleri <xref:System.ValueType>dışındaki türlerden devralınabilir, ancak arabirimler uygulayabilir, bu nedenle bir arabirim kullanmak ortak bir temel tür sağlamak için tek seçenektir.

 ✔️, bazı ortak API 'leri değer türlerini içeren bir tür kümesi tarafından desteklenmelidir.

 daha önce başka bir türden daha önce devraldığı türler üzerinde işlevselliğini desteklemeniz gerekiyorsa, bir arabirim tanımlamayı düşünün ✔️.

 ❌ işaretçi arabirimlerini kullanmaktan kaçının (üye olmayan arabirimler).

 Bir sınıfı belirli bir özelliğe (işaret) sahip olacak şekilde işaretlemeniz gerekiyorsa, genel olarak, bir arabirim yerine özel bir öznitelik kullanın.

 ✔️, bir arabirimin uygulanması olan en az bir tür sağlar.

 Bunu yapmak, arabirimin tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.IList%601> arabiriminin bir uygulamasıdır.

 ✔️, tanımladığınız her arabirimi tüketen en az bir API (bir parametre olarak arabirimi veya arabirim olarak yazılmış bir özellik) sağlar.

 Bunu yapmak, arabirim tasarımını doğrulamaya yardımcı olur. Örneğin, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> arabirimini tüketir.

 ❌, daha önce sevk edilen bir arabirime üye eklemez.

 Bunun yapılması, arabirimin uygulamalarını bozar. Sürüm oluşturma sorunlarından kaçınmak için yeni bir arabirim oluşturmanız gerekir.

 Bu kılavuzlar bölümünde açıklanan durumlar haricinde, genel olarak, yönetilen kod yeniden kullanılabilir kitaplıklarını tasarlarken arabirimler yerine sınıfları seçin.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
