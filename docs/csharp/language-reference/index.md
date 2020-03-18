---
title: C# başvurusu
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 4875e53327e24c4b5983a4a3b79b5beced368725
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428609"
---
# <a name="c-reference"></a>C# başvurusu

Bu bölümde C# anahtar kelimeleri, işleçler, özel karakterler, önişlemci yönergeleri, derleyici seçenekleri ve derleyici hataları ve uyarıları hakkında referans materyali sağlanmıştır.  
  
## <a name="in-this-section"></a>Bu bölümde

 [C# Anahtar Kelimeler](./keywords/index.md)  
 C# anahtar kelimeleri ve sözdizimi hakkındaki bilgilere bağlantılar sağlar.  
  
 [C# Operatörleri](./operators/index.md)  
 C# işleçleri ve sözdizimi hakkındaki bilgilere bağlantılar sağlar.  

 [C# Özel Karakterleri](./tokens/index.md)  
 C# daki özel bağlamsal karakterler ve bunların kullanımı hakkında bilgilere bağlantılar sağlar.  

 [C# Önİşleme İşlemciler Direktifleri](./preprocessor-directives/index.md)  
 C# kaynak koduna katıştırmak için derleyici komutları hakkındaki bilgilere bağlantılar sağlar.  
  
 [C# Derleyici Seçenekleri](./compiler-options/index.md)  
 Derleyici seçenekleri ve bunların nasıl kullanılacağı hakkında bilgi içerir.  
  
 [C# Derleyici Hataları](./compiler-messages/index.md)  
 C# derleyici hatalarının ve uyarılarının nedenini ve düzeltmesini gösteren kod parçacıkları içerir.  
  
 [C# Dil Belirtimi](../../../_csharplang/spec/introduction.md)  
 C# 6.0 dil belirtimi. Bu C# 6.0 dili için bir taslak öneridir. Bu belge ECMA C# standartları komitesi ile yapılacak çalışmalarla rafine edilecektir. Sürüm 5.0, Aralık 2017'de [Standart ECMA-334 5th Edition](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) belgesi olarak yayımlanmıştır.

6.0'dan sonra C# sürümlerinde uygulanan özellikler dil belirtimi önerilerinde temsil edilir. Bu belgeler, bu yeni özellikleri eklemek için dil spec deltas açıklar. Bunlar taslak teklif formundadır. Bu özellikler geliştirilecek ve resmi inceleme için ECMA standartlar komitesine sunulacak ve C# Standard'ın gelecekteki bir sürümüne dahil edilecektir.

 [C# 7.0 Şartname Önerileri](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 C# 7.0'da uygulanan bir dizi yeni özellik vardır. Bunlar desen eşleştirme, yerel işlevler, değişken bildirimleri, atmak ifadeleri, ikili literals ve basamak ayırıcıları içerir. Bu klasör, bu özelliklerin her biri için belirtimleri içerir.
  
 [C# 7.1 Şartname Önerileri](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 C# 7.1'de eklenen yeni özellikler vardır. İlk olarak, döndürür `Main` `Task` veya `Task<int>`bir yöntem yazabilirsiniz. Bu, değiştiricinin `async` `Main`. İfade, `default` türün çıkarılabildiği konumlarda bir tür olmadan kullanılabilir. Ayrıca, tuple üye adları çıkarılabilir. Son olarak, desen eşleştirme jenerik ile kullanılabilir.

 [C# 7.2 Şartname Önerileri](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7.2 bir dizi küçük özellik ekledi. Anahtar kelimeyi kullanarak bağımsız değişkenleri yalnızca başvuruyu okuyarak `in` geçirebilirsiniz. Derleme zamanı güvenliğini ve ilgili türleri desteklemek için `Span` bir dizi düşük düzeyli değişiklik vardır. Bazı durumlarda, daha sonraki bağımsız değişkenlerin konumsal olduğu adlandırılmış bağımsız değişkenleri kullanabilirsiniz. Erişim `private protected` değiştiricisi, arayanların aynı derlemede uygulanan türetilmiş türlerle sınırlı olduğunu belirtmenize olanak tanır. İşleç `?:` bir değişkene bir başvuru çözebilir. Ayrıca, önde gelen bir basamak ayırıcısı kullanarak hexadecimal ve ikili sayıları biçimlendirebilirsiniz.

 [C# 7.3 Şartname Önerileri](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C# 7.3 birkaç küçük güncelleştirmeiçeren başka bir nokta yayımı. Genel tür parametreleri üzerinde yeni kısıtlamalar kullanabilirsiniz. Diğer değişiklikler, ayırmaları kullanma `fixed` [`stackalloc`](./operators/stackalloc.md) da dahil olmak üzere alanlar ile çalışmayı kolaylaştırır. `ref` Anahtar kelimeyle bildirilen yerel değişkenler, yeni depolama alanına başvurmak üzere yeniden atanabilir. Öznitelikleri, derleyici tarafından oluşturulan destek alanını hedefleyen otomatik olarak uygulanan özelliklere yerleştirebilirsiniz. İfade değişkenleri başharflerinde kullanılabilir. Tuples eşitlik (veya eşitsizlik) için karşılaştırılabilir. Ayrıca aşırı yükleme çözünürlüğü için bazı iyileştirmeler olmuştur.
  
 [C# 8.0 Şartname Önerileri](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C# 8.0 .NET Core 3.0 ile kullanılabilir. Bu özellikler, nullable başvuru türleri, özyinelemeli desen eşleştirme, varsayılan arabirim yöntemleri, async akışları, aralıkları ve dizinleri, desenleri kullanarak ve kullanarak desen tabanlı, null birleştirme atama ve yalnızca örnek üyeleri içerir.
  
## <a name="related-sections"></a>İlgili Bölümler  

 [C# için Visual Studio Geliştirme Ortamını Kullanma](/visualstudio/get-started/csharp)  
 IDE ve Düzenleyici'yi açıklayan kavramsal ve görev konularına bağlantılar sağlar.  
  
 [C# Programlama Kılavuzu](../programming-guide/index.md)  
 C# programlama dilinin nasıl kullanılacağı hakkında bilgi içerir.
