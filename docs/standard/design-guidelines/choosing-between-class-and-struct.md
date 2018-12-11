---
title: Sınıf ile yapı arasında seçim yapma
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
author: KrzysztofCwalina
ms.openlocfilehash: 650acf0efaa88120678819b77b03fab61107c630
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131332"
---
# <a name="choosing-between-class-and-struct"></a>Sınıf ile yapı arasında seçim yapma
Her framework Tasarımcısı yüz temel tasarım kararlarından biri mi (bir başvuru türü) bir sınıf veya yapı (bir değer türü) olarak bir tür tasarlamak biridir. Başvuru türleri ve değer türlerinin davranış farklılıkları iyi anlaşılmasını, bu seçim yaparken önemlidir.  
  
 İlk yığın başvuru türleri ve değer türleri biz başvuru türleri ise, değer türleri yığın üzerinde ayrılan veya içeren satır içi türleri ve ne zaman serbest ve atık toplanan yığında ayrılmış olmasıdır dikkate alacaktır fark geriye doğru alır veya ne zaman, içeren türlerine serbest bırakıldı. Bu nedenle, genel ayırma ve başvuru türleri deallocations ucuz ayırmaları ve değer türlerinin deallocations altındadır.  
  
 Ardından, diziler başvuru türleridir çıkış dizi anlamı satır dışı, yalnızca başvuru yığında bulunan başvuru türünün örneğini tahsis edilir. Değer türü diziler, dizi öğelerinin değer türü gerçek örneklerini olduğu anlamına satır içi, ayrılır. Bu nedenle, ayırma ve değer türü diziler deallocations ayırmaları ve başvuru türü diziler deallocations ucuz. Ayrıca, çoğu durumda, değer türü diziler çok daha iyi bir yerleşim yeri başvuru sergiler.  
  
 Sonraki farka bellek kullanımı ile ilgilidir. Değer türleri, bir başvuru türü veya uyguladıkları arabirimlerinden birini olduğunda cast Kutulu. Kutulanmamış aldıkları ne zaman değer türüne dönüştürme. Kutuları yığında ayrılır ve atık olarak toplanmış, çok fazla kutulama ve kutudan çıkarma nesneler olduğundan, yığın, atık toplayıcı ve nihai olarak uygulamanın performansı üzerinde olumsuz bir etkiye sahip olabilir.  Buna karşılık, başvuru türleri dönüştürme gibi böyle bir kutulama gerçekleşir. (Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../csharp/programming-guide/types/boxing-and-unboxing.md)).
  
 Ardından, değer türü atamaları tüm değeri kopyalayın ise başvuru türü atamaları başvuru kopyalayın. Bu nedenle, büyük referans tür atamaları büyük değer türlerinin atamaları ucuz.  
  
 Son olarak, değer türleri değere göre geçirilir ancak başvuru türleri başvuruya göre iletilir. Bir başvuru türünün örneğini yapılan değişiklikler tüm başvuruları örneğine işaret etkiler. Değer türü örnekleri değere göre geçirildiğinde kopyalanır. Bir değer türü örneği değiştirildiğinde, Elbette herhangi birini kendi kopya etkilemez. Kopya açıkça kullanıcı tarafından oluşturulmaz, ancak bağımsız değişkenler geçirilir veya dönüş değerleri döndürülür, örtük olarak oluşturulur, değiştirilebilir bir değer türleri birçok kullanıcılar için kafa karıştırıcı olabilir. Bu nedenle, değer türleri sabit olmalıdır.  
  
 Bir kural karşısında, bir Framework türlerinin çoğu sınıflar olmalıdır. Ancak, bir değer türü özelliklerini yapıları kullanmak daha uygun hale bazı durumlar vardır.  
  
 **✓ CONSIDER** türünün örnekleri küçük ve yaygın olarak kısa süreli veya diğer nesneleri genellikle katıştırılmış yapı yerine bir sınıf tanımlama.  
  
 **X AVOID** türü tüm aşağıdaki özelliklere sahip olmadığı sürece yapı tanımlama:  
  
-   Mantıksal olarak, ilkel türler için benzer tek bir değeri temsil eder (`int`, `double`vb..).  
  
-   Bir örnek boyutu altında 16 bayt var.  
  
-   Sabittir.  
  
-   Bu sık Kutulu gerekmez.  
  
 Diğer tüm durumlarda, türlerinizi sınıfları olarak tanımlamanız gerekir.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
