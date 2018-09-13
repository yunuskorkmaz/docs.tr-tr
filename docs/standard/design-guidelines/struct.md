---
title: Yapı tasarımı
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
ms.openlocfilehash: 3879dc3f0270a56132b44882a74c50d05914ff89
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709577"
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
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Tür Tasarımı Yönergeleri](../../../docs/standard/design-guidelines/type.md)  
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Sınıf ile Yapı Arasında Seçim Yapma](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
