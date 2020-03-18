---
title: deyimi kullanarak - C# Reference
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712968"
---
# <a name="using-statement-c-reference"></a>deyimi kullanarak (C# Reference)

<xref:System.IDisposable> Nesnelerin doğru kullanımını sağlayan kullanışlı bir sözdizimi sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, deyimin `using` nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

C# 8.0 ile başlayarak, ayraç gerektirmeyen `using` ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Açıklamalar

<xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlere örneklerdir (bu durumda dosya işletmek ve aygıt bağlamları). Yönetilmeyen kaynakların ve bunları kapsülleyen sınıf kitaplık türlerinin başka türleri de vardır. Tüm bu tür <xref:System.IDisposable> arabirimi uygulamak gerekir.

Bir `IDisposable` nesnenin ömrü tek bir yöntemle sınırlıysa, `using` bunu ifadede beyan etmeli ve anında bildirmelisiniz. Deyim, `using` nesne <xref:System.IDisposable.Dispose%2A> üzerindeki yöntemi doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda) nesnenin kendisini de <xref:System.IDisposable.Dispose%2A> çağrıldığı anda kapsam dışına çıkmasına neden olur. `using` Blok içinde, nesne salt okunur ve değiştirilemez veya yeniden atanamaz.

İfade, `using` `using` blok <xref:System.IDisposable.Dispose%2A> içinde bir özel durum oluşsa bile bunun çağrılmasını sağlar. Nesneyi bir `try` bloğun içine koyup bir <xref:System.IDisposable.Dispose%2A> `finally` bloğu arayarak aynı sonuca ulaşabilirsiniz; aslında, `using` bu nasıl ifade derleyici tarafından tercüme edilir. Kod örneği daha önce derleme zamanında aşağıdaki koda genişletir (nesne için sınırlı kapsamı oluşturmak için ekstra kıvırcık ayraçlara dikkat edin):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Yeni `using` ifade sözdizimi çok benzer koda çevirir. Blok, `try` değişkenin beyan edildiği yerde açılır. Blok, `finally` genellikle bir yöntemin sonunda, çevreleyen bloğun kapanışına eklenir.

İfade hakkında `try` - daha fazla bilgi [için, try-finally](try-finally.md) konusuna bakın. `finally`

Aşağıdaki örnekte gösterildiği gibi, `using` bir türün birden çok örneği deyimde bildirilebilir:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

C# 8 ile tanıtılan yeni sözdizimini kullanarak aynı türdeki birden çok bildirimi de birleştirebilirsiniz. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Kaynak nesnesini anında anlayabilir ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi uygulama değildir. Bu durumda, denetim `using` bloğu terk ettikten sonra, nesne kapsamda kalır, ancak büyük olasılıkla yönetilmeyen kaynaklarına erişimi yoktur. Başka bir deyişle, artık tam olarak başharfe biçilemedi. Nesneyi `using` bloğun dışında kullanmaya çalışırsanız, bir özel durum atılmasını göze alabilirsiniz. Bu nedenle, `using` genellikle ifadedeki nesneyi anında anlayıp kapsamını blokla `using` sınırlamak genellikle daha iyidir.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

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
