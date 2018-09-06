---
title: Sınıf ile yapı arasında seçim yapma
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06661cb2c34d1da9085fa2129cb0c3307b99097e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865559"
---
# <a name="choosing-between-class-and-struct"></a>Sınıf ile yapı arasında seçim yapma
Her framework Tasarımcısı yüz temel tasarım kararlarından biri mi (bir başvuru türü) bir sınıf veya yapı (bir değer türü) olarak bir tür tasarlamak biridir. Başvuru türleri ve değer türlerinin davranış farklılıkları iyi anlaşılmasını, bu seçim yaparken önemlidir.  
  
 İlk yığın başvuru türleri ve değer türleri biz başvuru türleri ise, değer türleri yığın üzerinde ayrılan veya içeren satır içi türleri ve ne zaman serbest ve atık toplanan yığında ayrılmış olmasıdır dikkate alacaktır fark geriye doğru alır veya ne zaman, içeren türlerine serbest bırakıldı. Bu nedenle, genel ayırma ve başvuru türleri deallocations ucuz ayırmaları ve değer türlerinin deallocations altındadır.  
  
 Ardından, diziler başvuru türleridir çıkış dizi anlamı satır dışı, yalnızca başvuru yığında bulunan başvuru türünün örneğini tahsis edilir. Değer türü diziler, dizi öğelerinin değer türü gerçek örneklerini olduğu anlamına satır içi, ayrılır. Bu nedenle, ayırma ve değer türü diziler deallocations ayırmaları ve başvuru türü diziler deallocations ucuz. Ayrıca, çoğu durumda, değer türü diziler çok daha iyi bir yerleşim yeri başvuru sergiler.  
  
 Sonraki farka bellek kullanımı ile ilgilidir. Değer türleri, bir başvuru türü veya uyguladıkları arabirimlerinden birini olduğunda cast Kutulu. Kutulanmamış aldıkları ne zaman değer türüne dönüştürme. Kutuları yığında ayrılır ve atık olarak toplanmış, çok fazla kutulama ve kutudan çıkarma nesneler olduğundan, yığın, atık toplayıcı ve nihai olarak uygulamanın performansı üzerinde olumsuz bir etkiye sahip olabilir.  Buna karşılık, başvuru türleri dönüştürme gibi böyle bir kutulama gerçekleşir.  
  
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
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
