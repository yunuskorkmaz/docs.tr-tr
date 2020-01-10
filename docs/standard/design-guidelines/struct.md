---
title: Yapı Tasarımı
ms.date: 10/22/2008
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
ms.openlocfilehash: 8841a30f1dd0420b2ea45740b1e33bde5199c3f9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709055"
---
# <a name="struct-design"></a>Yapı Tasarımı
Genel amaçlı değer türü, genellikle bir struct, C# anahtar kelimesi olarak adlandırılır. Bu bölüm, genel yapı tasarımı için yönergeler sağlar.  
  
 **X** bir struct için parametresiz bir Oluşturucu sağlamaz.  
  
 Bu kılavuzdan sonra, dizinin her öğesinde oluşturucuyu çalıştırmak zorunda kalmadan yapıların dizilerinin oluşturulmasına izin verir. Yapıların parametresiz C# oluşturuculara sahip olduğundan emin olun.  
  
 **X DO NOT** değişmez değer türleri tanımlayın.  
  
 Kesilebilir değer türlerinde birçok sorun vardır. Örneğin, bir özellik alıcısı bir değer türü döndürdüğünde, çağıran bir kopyasını alır. Kopya örtük olarak oluşturulduğundan, geliştiriciler özgün değeri değil, kopyayı değiştirmez gibi farkında olmayabilir. Ayrıca, bazı dillerin (özellikle de dinamik diller) değişebilir değer türlerini kullanarak sorunlar vardır, çünkü başvuru yapıldığında yerel değişkenler de bir kopyanın oluşturulmasına neden olur.  
  
 **✓ DO** veri tüm örnek olduğu bir duruma sıfıra ayarlanır ve yanlış veya boş (hangisi uygunsa) geçerli olduğundan emin.  
  
 Bu, yapıların bir dizisi oluşturulduğunda geçersiz örneklerin yanlışlıkla oluşturulmasını önler.  
  
 **✓ DO** uygulamak <xref:System.IEquatable%601> değer türleri üzerinde.  
  
 Değer türlerinde <xref:System.Object.Equals%2A?displayProperty=nameWithType> yöntemi kutulama sağlar ve yansıma kullandığından, varsayılan uygulama çok verimli değildir. <xref:System.IEquatable%601.Equals%2A> çok daha iyi bir performansa sahip olabilir ve bu, kutulamayı neden olmayacak şekilde uygulanabilir.  
  
 **X DO NOT** açıkça genişletmek <xref:System.ValueType>. Aslında çoğu dil bunu engeller.  
  
 Genel olarak, yapılar çok faydalı olabilir, ancak yalnızca sık kutulanmamış küçük, tek, sabit değerler için kullanılmalıdır.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Sınıf ile Yapı Arasında Seçim Yapma](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
