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
author: KrzysztofCwalina
ms.openlocfilehash: e787c5b34848a561b43c3457341673f11cc2bd00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775550"
---
# <a name="struct-design"></a>Yapı Tasarımı
Genel amaçlı bir değer türü, genellikle kendi C# anahtar sözcüğü bir yapı da adlandırılır. Bu bölümde, genel yapı tasarımı için yönergeler sağlar.  
  
 **X yok** parametresiz bir oluşturucu için bir yapı sağlar.  
  
 Bu kılavuz aşağıdaki dizinin her öğesinde Oluşturucusu çalıştırmak zorunda kalmadan oluşturulacak yapı dizileri sağlar. Dikkat C# parametresiz oluşturucular yapılar izin vermiyor.  
  
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
