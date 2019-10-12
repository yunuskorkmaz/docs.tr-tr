---
title: C#Başvurunun
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: df56287d161f7760e136eb80aa1a9171966df794
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275805"
---
# <a name="c-reference"></a>C#Başvurunun
Bu bölümde, anahtar sözcükler, C# işleçler, özel karakterler, Önişlemci yönergeleri, derleyici seçenekleri ve derleyici hataları ve uyarıları hakkında başvuru malzemeleri sağlanmaktadır.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [C#Lerimi](./keywords/index.md)  
 Anahtar sözcükler ve sözdizimi hakkında C# bilgi için bağlantılar sağlar.  
  
 [C#İşletmenlerinin](./operators/index.md)  
 İşleçler ve sözdizimi hakkında C# bilgi için bağlantılar sağlar.  

 [C#Özel karakterler](./tokens/index.md)  
 ' Deki C# özel bağlamsal karakterler ve kullanımları hakkındaki bilgilerin bağlantılarını sağlar.  

 [C#Önişlemci yönergeleri](./preprocessor-directives/index.md)  
 C# Kaynak koda ekleme için derleyici komutları hakkındaki bilgilere bağlantılar sağlar.  
  
 [C#Derleyici seçenekleri](./compiler-options/index.md)  
 Derleyici seçenekleri ve bunların nasıl kullanılacağı hakkında bilgi içerir.  
  
 [C#Derleyici hataları](./compiler-messages/index.md)  
 C# Derleyici hatalarının ve uyarılarının nedenini ve düzeltmesini gösteren kod parçacıkları içerir.  
  
 [C#Dil belirtimi](../../../_csharplang/spec/introduction.md)  
 C# 6,0 dil belirtimi. Bu, C# 6,0 diline yönelik taslak bir önersahiptir. Bu belge, ECMA C# standartları Komitesi ile çalışma aracılığıyla iyileştirilcektir. Sürüm 5,0, [standart ECMA-334 5 sürümü](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) belgesi olarak 2017 Aralık 'ta yayımlanmıştır.

6,0 sonrası C# sürümlerde uygulanan özellikler, dil belirtimi tekliflerinde temsil edilir. Bu belgeler, bu yeni özellikleri eklemek için dil belirtimine yönelik değişimleri ' i anlatmaktadır. Bunlar taslak teklif formundadır. Bu belirtimler, resmi İnceleme için ECMA standartları Komitesi ve kurulduğu 'in C# gelecekteki bir sürümüne gönderilir.

 [C#7,0 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 7,0 ' de C# uygulanan çeşitli yeni özellikler vardır. Bunlar, model eşleştirme, yerel işlevler, çıkış değişkeni bildirimleri, throw ifadeleri, ikili sabit değerler ve basamak ayırıcıları içerirler. Bu klasör, bu özelliklerin her biri için belirtimleri içerir.
  
 [C#7,1 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 7,1 ' C# ye eklenen yeni özellikler vardır. İlk olarak, `Task` veya `Task<int>` döndüren `Main` yöntemi yazabilirsiniz. Bu, `async` değiştiricisini `Main` ' e eklemenizi sağlar. @No__t-0 ifadesi, türün çıkarsanbileceği konumlarda bir tür olmadan kullanılabilir. Ayrıca demet üye adları da çıkarsanamıyor. Son olarak, bir model eşleştirme, genel türler ile kullanılabilir.

 [C#7,2 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C#7,2 çok sayıda küçük özellik ekledi. @No__t-0 anahtar sözcüğünü kullanarak, ReadOnly başvuruya göre bağımsız değişkenler geçirebilirsiniz. @No__t-0 ve ilgili türler için derleme zamanı güvenliğini desteklemeye yönelik bir dizi alt düzey değişiklik vardır. Bazı durumlarda, sonraki bağımsız değişkenlerin konumsal olduğu adlandırılmış bağımsız değişkenleri kullanabilirsiniz. @No__t-0 erişim değiştiricisi, arayanların aynı derlemede uygulanan türetilmiş türlerle sınırlı olduğunu belirtmenizi sağlar. @No__t-0 işleci bir değişkene bir başvuruya çözümleyebilir. Ayrıca, baştaki basamak ayırıcısını kullanarak onaltılık ve ikili sayıları biçimlendirebilirsiniz.

 [C#7,3 belirtim teklifleri](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C#7,3, birkaç küçük güncelleştirme içeren başka bir nokta sürümüdür. Yeni kısıtlamaları genel tür parametreleri üzerinde kullanabilirsiniz. Diğer değişiklikler, [`stackalloc`](./operators/stackalloc.md) ayırma kullanımı dahil `fixed` alanlarıyla çalışmayı kolaylaştırır. @No__t-0 anahtar sözcüğüyle belirtilen yerel değişkenler, yeni depolama alanına başvurmak için reasssigned olabilir. Öznitelikleri, derleyicinin ürettiği yedekleme alanını hedefleyen otomatik uygulanan özelliklere yerleştirebilirsiniz. , Başlatıcılarda ifade değişkenleri kullanılabilir. Tanımlama grupları, eşitlik (veya eşitsizlik) için karşılaştırılabilir. Aşırı yükleme çözümlemesi için bazı geliştirmeler de vardır.
  
 [C#8,0 belirtim teklifleri](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C#8,0, .NET Core 3,0 ile kullanılabilir. Özellikler, null yapılabilir başvuru türleri, özyinelemeli model eşleştirme, varsayılan arabirim yöntemleri, zaman uyumsuz akışlar, aralıklar ve dizinler, using bildirimleri kullanarak ve using bildirimlerini, null birleştirme atamasını ve salt okunur örnek üyelerini içerir.
  
## <a name="related-sections"></a>İlgili bölümler  

 [C#Rehberi](../index.md)  
 Görsel C# belgeler için bir portal sağlar.  
  
 [İçin Visual Studio geliştirme ortamını kullanmaC#](/visualstudio/get-started/csharp)  
 IDE ve düzenleyiciyi tanımlayan kavramsal ve görev konularına bağlantılar sağlar.  
  
 [C#Programlama Kılavuzu](../programming-guide/index.md)  
 C# Programlama dilinin kullanımı hakkındaki bilgileri içerir.
