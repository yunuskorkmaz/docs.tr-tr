---
description: C# başvurusu
title: C# başvurusu
ms.date: 02/14/2017
f1_keywords:
- _CSharpKeyword
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: 317f375c46eee3bb9c719afb68993cd4720e54fe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127197"
---
# <a name="c-reference"></a>C# başvurusu

Bu bölümde C# anahtar kelimeleri, işleçler, özel karakterler, Önişlemci yönergeleri, derleyici seçenekleri ve derleyici hataları ve uyarıları hakkında başvuru malzemeleri sağlanmaktadır.  
  
## <a name="in-this-section"></a>Bu bölümde

 [C# anahtar sözcükleri](./keywords/index.md)  
 C# anahtar kelimeleri ve sözdizimi hakkında bilgi için bağlantılar sağlar.  
  
 [C# işleçleri](./operators/index.md)  
 C# işleçleri ve sözdizimi hakkında bilgi bağlantıları sağlar.  

 [C# özel karakterleri](./tokens/index.md)  
 C# ve kullanımları için özel bağlamsal karakterler hakkında bilgi bağlantıları sağlar.  

 [C# Önişlemci yönergeleri](./preprocessor-directives/index.md)  
 C# kaynak kodunda ekleme için derleyici komutları hakkındaki bilgilere bağlantılar sağlar.  
  
 [C# derleyici seçenekleri](./compiler-options/index.md)  
 Derleyici seçenekleri ve bunların nasıl kullanılacağı hakkında bilgi içerir.  
  
 [C# derleyici hataları](./compiler-messages/index.md)  
 C# derleyici hatalarının ve uyarılarının nedenini ve düzeltmesini gösteren kod parçacıkları içerir.  
  
 [C# dil belirtimi](../../../_csharplang/spec/introduction.md)  
 C# 6,0 dil belirtimi. Bu, C# 6,0 diline yönelik taslak bir önersahiptir. Bu belge, ECMA C# standartları Komitesi ile çalışma aracılığıyla iyileştirilmelidir. Sürüm 5,0, [standart ECMA-334 5 sürümü](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) belgesi olarak 2017 Aralık 'ta yayımlanmıştır.

6,0 sonrasında C# sürümlerinde uygulanan özellikler, dil belirtimi tekliflerinde temsil edilir. Bu belgeler, bu yeni özellikleri eklemek için dil belirtimine yönelik değişimleri ' i anlatmaktadır. Bunlar taslak teklif formundadır. Bu belirtimler, resmi İnceleme için ECMA standartları Komitesi ve C# standardının gelecek bir sürümüne kurulduğu gönderilir.

 [C# 7,0 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 C# 7,0 ' de uygulanan çeşitli yeni özellikler vardır. Bunlar, model eşleştirme, yerel işlevler, çıkış değişkeni bildirimleri, throw ifadeleri, ikili sabit değerler ve basamak ayırıcıları içerirler. Bu klasör, bu özelliklerin her biri için belirtimleri içerir.
  
 [C# 7,1 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 C# 7,1 ' ye eklenen yeni özellikler vardır. İlk olarak, `Main` veya döndüren bir yöntem yazabilirsiniz `Task` `Task<int>` . Bu, değiştiricisini eklemenize olanak sağlar `async` `Main` . `default`İfade, türün çıkarsanbileceği konumlarda bir tür olmadan kullanılabilir. Ayrıca demet üye adları da çıkarsanamıyor. Son olarak, bir model eşleştirme, genel türler ile kullanılabilir.

 [C# 7,2 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7,2, çok sayıda küçük özellik ekledi. Anahtar sözcüğünü kullanarak, ReadOnly başvuruya göre bağımsız değişkenleri geçirebilirsiniz `in` . Ve ilgili türler için derleme zamanı güvenliğini desteklemeye yönelik bir dizi alt düzey değişiklik vardır `Span` . Bazı durumlarda, sonraki bağımsız değişkenlerin konumsal olduğu adlandırılmış bağımsız değişkenleri kullanabilirsiniz. `private protected`Erişim değiştiricisi, arayanların aynı derlemede uygulanan türetilmiş türlerle sınırlı olduğunu belirtmenizi sağlar. `?:`İşleci, bir değişkene bir başvuruya çözüm verebilir. Ayrıca, baştaki basamak ayırıcısını kullanarak onaltılık ve ikili sayıları biçimlendirebilirsiniz.

 [C# 7,3 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C# 7,3, birkaç küçük güncelleştirme içeren başka bir nokta sürümüdür. Yeni kısıtlamaları genel tür parametreleri üzerinde kullanabilirsiniz. Diğer değişiklikler `fixed` , ayırmaların kullanılması dahil olmak üzere alanlarla çalışmayı kolaylaştırır [`stackalloc`](./operators/stackalloc.md) . Anahtar sözcükle belirtilen yerel değişkenler, `ref` Yeni depolama birimine başvuracak şekilde yeniden atanabilir. Öznitelikleri, derleyicinin ürettiği yedekleme alanını hedefleyen otomatik uygulanan özelliklere yerleştirebilirsiniz. , Başlatıcılarda ifade değişkenleri kullanılabilir. Tanımlama grupları, eşitlik (veya eşitsizlik) için karşılaştırılabilir. Aşırı yükleme çözümlemesi için bazı geliştirmeler de vardır.
  
 [C# 8,0 belirtim teklifleri](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C# 8,0, .NET Core 3,0 ile kullanılabilir. Özellikler, null yapılabilir başvuru türleri, özyinelemeli model eşleştirme, varsayılan arabirim yöntemleri, zaman uyumsuz akışlar, aralıklar ve dizinler, using bildirimleri kullanarak ve using bildirimlerini, null birleştirme atamasını ve salt okunur örnek üyelerini içerir.
  
## <a name="related-sections"></a>İlgili bölümler  

 [C# için Visual Studio Geliştirme Ortamını Kullanma](/visualstudio/get-started/csharp)  
 IDE ve düzenleyiciyi tanımlayan kavramsal ve görev konularına bağlantılar sağlar.  
  
 [C# Programlama Kılavuzu](../programming-guide/index.md)  
 C# programlama dilinin kullanımı hakkındaki bilgileri içerir.
