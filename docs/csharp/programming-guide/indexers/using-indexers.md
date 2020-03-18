---
title: Dizin Oluşturma - C# Programlama Kılavuzunu Kullanma
ms.date: 10/03/2018
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: 17162a0dc959a85c03a5cb5757e2b91fe10b0ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628169"
---
# <a name="using-indexers-c-programming-guide"></a>Dizin oluşturma (C# Programlama Kılavuzu) kullanma

Dizin oluşturierler, istemci uygulamalarının bir dizi gibi erişebileceği bir [sınıf,](../../language-reference/keywords/class.md) [yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) oluşturmanıza olanak tanıyan bir sözdizimi kolaylığıdır. Dizin leyiciler en sık birincil amacı bir iç koleksiyon veya dizi kapsüllemek için türleri uygulanır. Örneğin, 24 saatlik `TempRecord` bir süre içinde 10 farklı zamanlarda kaydedilen Fahrenhayt sıcaklığını temsil eden bir sınıfolduğunu varsayalım. Sınıf, sıcaklık `temps` değerlerini `float[]` depolamak için bir dizi tür içerir. Bu sınıfta bir dizinleyici uygulayarak, istemciler `TempRecord` gibi `float temp = tr.temps[4]` `float temp = tr[4]` bir örnekte sıcaklıklara erişebilirsiniz . Dizinleyici gösterimi yalnızca istemci uygulamaları için sözdizimini basitleştirmekle kalmıyor; aynı zamanda sınıfı ve amacını diğer geliştiricilerin anlaması için daha sezgisel hale getirir.  
  
Bir sınıf veya yapı üzerinde bir dizinleyici bildirmek için, aşağıdaki örnekte görüldüğü gibi [bu](../../language-reference/keywords/this.md) anahtar kelimeyi kullanın:

```csharp
public int this[int index]    // Indexer declaration  
{  
    // get and set accessors  
}  
```

## <a name="remarks"></a>Açıklamalar

Dizinleyicinin türü ve parametrelerinin türü en az dizinleyicinin kendisi kadar erişilebilir olmalıdır. Erişilebilirlik düzeyleri hakkında daha fazla bilgi için [erişim değiştiricilere](../../language-reference/keywords/access-modifiers.md)bakın.  
  
 Arabirimli dizinleyicilerin nasıl kullanılacağı hakkında daha fazla bilgi için [Interface Indexers'a](./indexers-in-interfaces.md)bakın.  
  
 Bir dizinleyicinin imzası, biçimsel parametrelerinin sayısı ve türlerinden oluşur. Dizinleyici türünü veya resmi parametrelerin adlarını içermez. Aynı sınıfta birden fazla dizinleyici bildirirseniz, farklı imzaları olmalıdır.  
  
 Bir dizinleyici değeri değişken olarak sınıflandırılmaz; bu nedenle, [bir dizinleyici](../../language-reference/keywords/ref.md) değeri bir ref veya [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçemez.  
  
 Dizin leyiciye diğer dillerin kullanabileceği bir <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>ad sağlamak için aşağıdaki örnekte görüldüğü gibi kullanın:  

```csharp
[System.Runtime.CompilerServices.IndexerName("TheItem")]  
public int this[int index]   // Indexer declaration  
{
    // get and set accessors  
}  
```

Bu dizinleyici nin `TheItem`adı olacaktır. Ad özniteliğinin sağlanmaması `Item` varsayılan adı yapar.  
  
## <a name="example-1"></a>Örnek 1  
  
Aşağıdaki örnek, özel bir dizi alanının `temps`ve dizinleyicinin nasıl bildirilen gösterir. Dizinleyici, örneğe `tempRecord[i]`doğrudan erişim sağlar. Dizinleyici kullanmanın alternatifi, diziyi [genel](../../language-reference/keywords/public.md) üye olarak bildirmek `tempRecord.temps[i]`ve üyelerine doğrudan erişmektir.  
  
 Bir dizin göstericinin erişimi değerlendirildiğinde (örneğin, bir `Console.Write` bildirimde [olsun,](../../language-reference/keywords/get.md) erişim ekive çağrıldığını unutmayın. Bu nedenle, `get` erişimci yoksa, derleme zamanı hatası oluşur.  
  
 [!code-csharp[csProgGuideIndexers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#1)]  
  
## <a name="indexing-using-other-values"></a>Diğer değerleri kullanarak dizin oluşturma

C# dizinleyici parametre türünü sonlu ile sınırlamaz. Örneğin, dizinleyicisi olan bir dize kullanmak yararlı olabilir. Böyle bir dizinleyici, koleksiyondaki dizeyi arayarak ve uygun değeri döndürerek uygulanabilir. Erişime girenler aşırı yüklenebileceğinden, dize ve tümsek sürümleri birlikte bulunabilir.  
  
## <a name="example-2"></a>Örnek 2  
  
Aşağıdaki örnek, haftanın günlerini depolayan bir sınıf bildirir. Bir `get` erişimci bir dize, bir gün adı alır ve karşılık gelen tamsayı döndürür. Örneğin, "Pazar" 0 döndürür, "Pazartesi" 1 döndürür, ve benzeri.  
  
 [!code-csharp[csProgGuideIndexers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#2)]  
  
## <a name="robust-programming"></a>Sağlam programlama

 Dizinleyicilerin güvenliği ve güvenilirliğinin geliştirilebildiği iki ana yol vardır:  
  
- Geçersiz bir dizin değerinde istemci kodu geçme olasılığını işlemek için bir tür hata işleme stratejisi dahil emin olun. Bu konunun önceki ilk örneğinde, TempRecord sınıfı, istemci kodunun dizinleyiciye geçirmeden önce girişi doğrulamasını sağlayan bir Uzunluk özelliği sağlar. Hata işleme kodunu dizinleyicinin içine de koyabilirsiniz. Dizinleyici erişime aday olduğunuz özel durumları kullanıcılariçin belgelediğinden emin olun.  
  
- [Get'in](../../language-reference/keywords/get.md) erişilebilirliğini ayarlayın ve erişime girenleri makul olduğu kadar kısıtlayıcı olarak [ayarlayın.](../../language-reference/keywords/set.md) Bu özellikle `set` erişimci için önemlidir. Daha fazla bilgi için [bkz.](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
