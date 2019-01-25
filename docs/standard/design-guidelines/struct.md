---
title: Yapı tasarımı
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
author: KrzysztofCwalina
ms.openlocfilehash: cc5b8d7effda31b0236477b217bccf5cf2137f8c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646613"
---
# <a name="struct-design"></a>Yapı tasarımı
Genel amaçlı bir değer türü, genellikle kendi C# anahtar sözcüğü bir yapı da adlandırılır. Bu bölümde, genel yapı tasarımı için yönergeler sağlar.  
  
 **X DO NOT** yapısı için varsayılan bir oluşturucu sağlayın.  
  
 Bu kılavuz aşağıdaki dizinin her öğesinde Oluşturucusu çalıştırmak zorunda kalmadan oluşturulacak yapı dizileri sağlar. C# varsayılan oluşturucular yapılar izin vermediğini unutmayın.  
  
 **X DO NOT** değişmez değer türleri tanımlayın.  
  
 Değişmez değer türleri, bazı sorunlar vardır. Örneğin, bir değer türü özellik alıcısı geri döndüğünde, çağıran bir kopyasını alır. Geliştiriciler, kopya örtük olarak oluşturulduğundan, bunlar kopya ve özgün değeri diziyi emin haberdar olmayabilir. Ayrıca, bazı diller (özellikle dinamik dilleri) yerel değişkenler, başvurusu kaldırıldığında bile, bir kopyalama yapılacak neden değişmez değer türleri kullanarak sorunları vardır.  
  
 **✓ DO** veri tüm örnek olduğu bir duruma sıfıra ayarlanır ve yanlış veya boş (hangisi uygunsa) geçerli olduğundan emin.  
  
 Struct'ın bir dizi oluşturulduğunda bu geçersiz örnekleri yanlışlıkla oluşturulmasını engeller.  
  
 **✓ DO** uygulamak <xref:System.IEquatable%601> değer türleri üzerinde.  
  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType> Yöntemi değer türleri üzerinde kutulama neden olur ve yansıma kullandığından, varsayılan uygulama çok verimli değildir. <xref:System.IEquatable%601.Equals%2A> çok daha iyi performans sahip olabilir ve böylece kutulama açmayacağını uygulanabilir.  
  
 **X DO NOT** açıkça genişletmek <xref:System.ValueType>. Aslında, çoğu dil bu engeller.  
  
 Genel olarak, yapılar çok kullanışlı olabilir, ancak yalnızca sık Kutulu değil küçük, tek, sabit değerler kullanılmalıdır.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Sınıf ile Yapı Arasında Seçim Yapma](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
