---
title: Sınıf ile Yapı Arasında Seçim Yapma
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
ms.openlocfilehash: 76042bef1475f2fdf14e309390dcba6654ccfaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741751"
---
# <a name="choosing-between-class-and-struct"></a>Sınıf ile Yapı Arasında Seçim Yapma
Temel tasarım kararlarından biri olan her çerçeve tasarlayıcı, bir türü Sınıf (başvuru türü) veya yapı (değer türü) olarak tasarlamayacağındır. Bu seçimi yapmak için başvuru türleri ve değer türleri davranışlarındaki farkları iyi anlamak çok önemlidir.

 Başvuru türleri ve değer türleri arasındaki ilk fark, başvuru türlerinin yığın ve atık toplama üzerinde ayrıldığı, ancak değer türlerinin yığın üzerinde ayrıldığı ya da yığın üzerinde serbest bırakıldığı ve yığın olduğunda serbest bırakıldığı durumlarda dikkate alınması gerektiğini düşüneceğiz. ya da içerdiği tür serbest bırakılır. Bu nedenle, değer türlerinin ayırmaları ve ayırması, genel bir ucuz 'da, başvuru türlerinin tahsislerini ve ayırmayı kaldırır.

 Daha sonra, başvuru türü dizileri satır dışı ayrılır, yani dizi öğeleri yalnızca yığında bulunan başvuru türünün örneklerine başvurudur. Değer türü dizileri satır içi olarak ayrılır, yani dizi öğeleri değer türünün gerçek örnekleridir. Bu nedenle, değer türü dizilerinin ayırmaları ve ayırmaları, başvuru türü dizilerinin ayırmaya ve ayırmaya göre çok daha ucuz. Bunlara ek olarak, çoğu durumda değer türü dizileri başvurunun çok daha iyi yer aldığı yeri gösterir.

 Sonraki fark, bellek kullanımıyla ilgilidir. Değer türleri, bir başvuru türüne veya uygulamadıkları arabirimlerden birine dönüştürme yaparken kutulanır. Değer türüne geri dönüştürme yapıldıklarında kutulanmamış alırlar. Kutular, yığında ayrılan ve atık olarak toplanmış olan nesneler olduğundan, çok fazla kutulama ve kutudan çıkarma yığın üzerinde olumsuz bir etkiye, çöp toplayıcısına ve sonuç olarak uygulamanın performansına sahip olabilir.  Buna karşılık, başvuru türleri atama olarak böyle bir kutulama gerçekleşmez. (Daha fazla bilgi için bkz. [kutulama ve kutudan](../../csharp/programming-guide/types/boxing-and-unboxing.md)çıkarma).

 Ardından, başvuru türü atamaları başvuruyu kopyalar, ancak değer türü atamaları tüm değeri kopyalar. Bu nedenle, büyük başvuru türlerinin atamaları büyük değer türlerinin atamalarından çok daha ucuz.

 Son olarak, başvuru türleri başvuruya göre geçirilir, ancak değer türleri değere göre geçirilir. Başvuru türünün bir örneğinde yapılan değişiklikler örneğe işaret eden tüm başvuruları etkiler. Değer türü örnekleri, değere göre geçirildiğinde kopyalanır. Bir değer türünün örneği değiştirildiğinde, kurs herhangi bir kopyasını etkilemez. Kopyalar Kullanıcı tarafından açıkça oluşturulmadığından ancak bağımsız değişkenler geçtiğinde veya dönüş değerleri döndürüldüğünde örtük olarak oluşturulduysa, değiştirilebilen değer türleri çok sayıda kullanıcıya kafa karıştırıcı olabilir. Bu nedenle, değer türleri sabit olmalıdır.

 Thumb kuralı olarak, bir çerçevede türlerin çoğunluğu sınıf olmalıdır. Ancak, bir değer türünün özelliklerinin yapıları kullanmak için daha uygun hale yaptığı bazı durumlar vardır.

 ✔️, türün örnekleri küçük ve genellikle kısa süreli ise veya genellikle diğer nesnelere katıştırılmışsa sınıf yerine bir struct tanımlamayı düşünün.

 tür aşağıdaki özelliklerin tümüne sahip olmadığı takdirde bir struct tanımlamaktan KAÇıNıN: ❌

- Temel türler (`int`, `double`, vb.) gibi tek bir değeri mantıksal olarak temsil eder.

- 16 baytlık bir örnek boyutu vardır.

- Bu sabittir.

- Sık olarak kutulanabilir olması gerekmez.

 Diğer tüm durumlarda türlerinizi sınıflar olarak tanımlamanız gerekir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
