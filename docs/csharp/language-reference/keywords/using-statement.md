---
title: deyimi kullanarak - C# Reference
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989187"
---
# <a name="using-statement-c-reference"></a>deyimi kullanarak (C# Reference)

<xref:System.IDisposable> Nesnelerin doğru kullanımını sağlayan kullanışlı bir sözdizimi sağlar. C# 8.0'dan `using` başlayarak, deyim <xref:System.IAsyncDisposable> nesnelerin doğru kullanımını sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, deyimin `using` nasıl kullanılacağını gösterir.

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

C# 8.0 ile başlayarak, ayraç gerektirmeyen `using` ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a>Açıklamalar

<xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlere örneklerdir (bu durumda dosya işletmek ve aygıt bağlamları). Yönetilmeyen kaynakların ve bunları kapsülleyen sınıf kitaplık türlerinin başka türleri de vardır. Tüm bu tür <xref:System.IDisposable> arabirimi veya <xref:System.IAsyncDisposable> arabirimi uygulamalıdır.

Bir `IDisposable` nesnenin ömrü tek bir yöntemle sınırlıysa, `using` bunu ifadede beyan etmeli ve anında bildirmelisiniz. Deyim, `using` nesne <xref:System.IDisposable.Dispose%2A> üzerindeki yöntemi doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda) nesnenin kendisini de <xref:System.IDisposable.Dispose%2A> çağrıldığı anda kapsam dışına çıkmasına neden olur. `using` Blok içinde, nesne salt okunur ve değiştirilemez veya yeniden atanamaz. Nesne yerine `IAsyncDisposable` `IDisposable`uygularsa, `using` deyimi çağırır <xref:System.IAsyncDisposable.DisposeAsync%2A> `awaits` ve <xref:System.Threading.Tasks.Task>döndürülür.

İfade, `using` <xref:System.IDisposable.Dispose%2A> `using` blok içinde <xref:System.IAsyncDisposable.DisposeAsync%2A>bir özel durum oluşsa bile (veya) çağrılmasını sağlar. Nesneyi `try` bir bloğun içine koyup (veya <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A> bir `finally` blokta; aslında `using` deyim derleyici tarafından bu şekilde çevrilmiştir) çağırarak aynı sonucu elde edebilirsiniz. Kod örneği daha önce derleme zamanında aşağıdaki koda genişletir (nesne için sınırlı kapsamı oluşturmak için ekstra kıvırcık ayraçlara dikkat edin):

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

Yeni `using` deyim sözdizimi benzer koda çevirir. Blok, `try` değişkenin beyan edildiği yerde açılır. Blok, `finally` genellikle bir yöntemin sonunda, çevreleyen bloğun kapanışına eklenir.

İfade hakkında `try` - daha fazla bilgi [için, try-finally](try-finally.md) makalesine bakın. `finally`

Bir türün birden çok örneği, `using` aşağıdaki örnekte gösterildiği gibi tek bir deyimle bildirilebilir. Tek bir ifadede birden çok değişken ilettiğinizde örtülü olarak yazılan değişkenleri ()`var`kullanamayacağınızı unutmayın:

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

Aşağıdaki örnekte gösterildiği gibi, C# 8 ile tanıtılan yeni sözdizimini kullanarak aynı türden birden çok bildirimi birleştirebilirsiniz:

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

Kaynak nesnesini anında anlayabilir ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi uygulama değildir. Bu durumda, denetim `using` bloğu terk ettikten sonra, nesne kapsamda kalır, ancak büyük olasılıkla yönetilmeyen kaynaklarına erişimi yoktur. Başka bir deyişle, artık tam olarak başharfe biçilemedi. Nesneyi `using` bloğun dışında kullanmaya çalışırsanız, bir özel durum atılmasını göze alabilirsiniz. Bu nedenle, `using` nesnenin ifadedeki anlık olarak anlık olarak ve kapsamını `using` blokla sınırlamak daha iyidir.

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

`IDisposable` Nesnelerin atılması hakkında daha fazla bilgi için [bkz.](../../../standard/garbage-collection/using-objects.md)

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [using deyimine](~/_csharplang/spec/statements.md#the-using-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [using Yönergesi](using-directive.md)
- [Çöp Toplama](../../../standard/garbage-collection/index.md)
- [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md)
- [IDisposable arayüzü](xref:System.IDisposable)
- [C# 8.0'da ifade kullanma](~/_csharplang/proposals/csharp-8.0/using.md)
