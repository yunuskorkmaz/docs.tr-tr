---
title: Sınıf ve yapı arasında seçim yapma
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
ms.openlocfilehash: 8bb05b825113c025781a790dc206d500633a3b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="choosing-between-class-and-struct"></a>Sınıf ve yapı arasında seçim yapma
Her framework Tasarımcısı bakarken temel tasarım kararlarından biri bir türü (bir başvuru türü) bir sınıf veya yapı (bir değer türü) olarak tasarlamanız verilip biridir. Başvuru türleri ve değer türlerini davranış farklılıkları iyi anlaşılmasını, bu seçenek yaparken önemlidir.  
  
 İlk yığın biz başvuru türleri değer türleri ya yığında ayrılan veya içeren içinde satır içi türleri ve ne zaman serbest ancak yığında ayrılmış ve atık toplanan olmasıdır değerlendirir değer türleri ve başvuru türleri arasında fark unwinds veya ne zaman, içeren türde serbest. Bu nedenle, genel ayırma ve başvuru türleri ayırma kaldırma işlemleri ucuz ayırma ve değer türlerini ayırma kaldırma işlemleri altındadır.  
  
 Ardından, başvuru türleri bir dizi genişletme öğeleri olan bir dizi anlamı satır sonu, öbek üzerinde bulunan başvuru türündeki örneklerin yalnızca başvurular tahsis edilir. Değer türü diziler satır içi dizi öğeleri değer türü gerçek örneklerini olduğu anlamına gelir, ayrılır. Bu nedenle, ayırma ve ayırma kaldırma işlemleri değer türü dizi ayırma ve başvuru türü dizi ayırma kaldırma işlemleri ucuz. Ayrıca, çoğu durumda değer türü diziler kadar daha iyi yere göre başvuru sergiler.  
  
 Sonraki fark bellek kullanımı ilişkilidir. Değer türleri, ne zaman bir başvuru türü veya uyguladıkları arabirimlerinden biri, cast Kutulu. Sarmalanmamış Al ne zaman değer türüne dönüştürün. Kutuları yığında ayrılmış ve atık olarak toplanmış, çok fazla kutulama ve kutudan çıkarma nesneler olduğundan öbek, atık toplayıcı ve sonuçta uygulamanın performansını olumsuz etkileyebilir olabilir.  Başvuru türleri cast olarak buna karşılık, böyle bir kutulama oluşur.  
  
 Ardından, tüm değer değer türü atamaları kopyalama ancak başvuru türü atamalarıyla başvuru kopyalayın. Bu nedenle, büyük referans tür atamaları büyük değer türleri atamaları ucuz.  
  
 Son olarak, değer türleri değeriyle geçirilir ancak başvuru türleri başvuruya göre geçirilir. Bir başvuru türünde bir örnek yapılan değişiklikler tüm başvuruları örneğini işaret etkiler. Değer türü örnekleri değeriyle geçirildiğinde kopyalanır. Bir değer türü örneği değiştirildiğinde, Elbette kendi kopyaları hiçbirini etkilemez. Kopya açıkça kullanıcı tarafından oluşturulmaz, ancak bağımsız değişkenler geçirilir ya da değerleri döndürülen dönüş örtük olarak oluşturulmuş olduğundan değiştirilebilir değer türleri birçok kullanıcılar için kafa karıştırıcı olabilir. Bu nedenle, değer türleri sabit olmalı.  
  
 Altın kural, bir çerçeve türlerinde çoğunluğu sınıfları olmalıdır. Bununla birlikte, içinde bir değer türü özelliklerini yapılar kullanmak daha uygun kolaylaştırır bazı durumlar vardır.  
  
 **✓ DÜŞÜNÜN** türünün örnekleri küçük ve yaygın olarak kısa süreli veya diğer nesneleri genellikle katıştırılmış yapı yerine bir sınıf tanımlama.  
  
 **KAÇININ x** türü tüm aşağıdaki özelliklere sahip olmadığı sürece yapı tanımlama:  
  
-   Mantıksal olarak, ilkel türler için benzer tek bir değeri temsil eder (`int`, `double`vb..).  
  
-   Bir örnek boyutu altında 16 bayt vardır.  
  
-   Değişmez.  
  
-   Bunu sık Kutulu gerekmez.  
  
 Diğer durumlarda, sınıflar türlerinizi tanımlamanız gerekir.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
