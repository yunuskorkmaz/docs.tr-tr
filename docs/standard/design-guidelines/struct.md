---
title: Yapı tasarım
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2621aa96cf89b453d5faec3357d0890ca36251d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="struct-design"></a>Yapı tasarım
Genel amaçlı değer türü, genellikle kendi C# anahtar sözcüğü bir yapı da adlandırılır. Bu bölüm için genel yapısı tasarım yönergeleri sağlar.  
  
 **X yok** yapısı için varsayılan bir oluşturucu sağlayın.  
  
 Bu kılavuz aşağıdaki Oluşturucusu dizinin her bir öğede çalıştırmak zorunda kalmadan oluşturulacak yapılar dizileri sağlar. C# varsayılan oluşturucular olmasını yapılar izin vermediğini unutmayın.  
  
 **X yok** değişmez değer türleri tanımlayın.  
  
 Değişmez değer türleri bazı sorunlar vardır. Örneğin, bir özellik Get yordamı bir değer türü geri döndüğünde, çağıran bir kopyasını alır. Kopya örtük olarak oluşturulduğundan, geliştiriciler, kopyalama ve özgün değeri diziyi, uyumlu olmayabilir. Ayrıca, bazı dillerde (özellikle dinamik dilleri) yerel değişkenler başvuru yapıldı olduğunda bile, yapılacak bir kopyasını neden olduğundan değişmez değer türleri kullanarak sorunları vardır.  
  
 **✓ YAPMAK** veri tüm örnek olduğu bir duruma sıfıra ayarlanır ve yanlış veya boş (hangisi uygunsa) geçerli olduğundan emin.  
  
 Yapılar dizisi oluşturulduğunda, bu geçersiz örnekleri yanlışlıkla oluşturulmasını engeller.  
  
 **✓ YAPMAK** uygulamak <xref:System.IEquatable%601> değer türleri üzerinde.  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType> Değer türleri üzerinde yöntemi kutulama neden olur ve yansıma kullandığından, varsayılan uygulama çok verimli değil. <xref:System.IEquatable%601.Equals%2A> çok daha iyi performans sağlayabilirsiniz ve böylece kutulama açmayacağını uygulanabilir.  
  
 **X yok** açıkça genişletmek <xref:System.ValueType>. Aslında, çoğu dilleri bu engeller.  
  
 Genel olarak, yapılar çok kullanışlı olabilir ancak yalnızca sık Kutulu olmayan küçük, tek, değişmez değerler kullanılmalıdır.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Sınıf ile Yapı Arasında Seçim Yapma](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
