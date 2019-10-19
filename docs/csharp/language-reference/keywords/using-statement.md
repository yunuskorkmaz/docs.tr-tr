---
title: using deyimleri- C# başvuru
ms.custom: seodec18
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7e6d1b663007d430f71f81923f343f1c43f5dd2d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579176"
---
# <a name="using-statement-c-reference"></a>using deyimleri (C# başvuru)

@No__t_0 nesnelerinin doğru kullanımını sağlayan uygun bir sözdizimi sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `using` deyimin nasıl kullanılacağını göstermektedir.

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

8,0 ile C# başlayarak, küme ayraçları gerektirmeyen `using` bildiri için aşağıdaki alternatif sözdizimini kullanabilirsiniz:

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a>Açıklamalar

<xref:System.IO.File> ve <xref:System.Drawing.Font>, yönetilmeyen kaynaklara erişen yönetilen türlerin örnekleridir (Bu durumda dosya tutamaçları ve cihaz bağlamları). Birçok farklı türde yönetilmeyen kaynak ve bunları kapsülleyen sınıf kitaplığı türleri vardır. Bu tür türler <xref:System.IDisposable> arabirimini gerçekleştirmelidir.

Bir `IDisposable` nesnesinin kullanım ömrü tek bir yöntemle sınırlıysa, bunu `using` bildiriminde bildirmeniz ve oluşturmanız gerekir. @No__t_0 ifade, nesne üzerinde <xref:System.IDisposable.Dispose%2A> yöntemini doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda), <xref:System.IDisposable.Dispose%2A> çağrıldığında nesnenin kendisinin kapsam dışına geçmesine da neden olur. @No__t_0 bloğunda, nesnesi salt okunurdur ve değiştirilemez ya da yeniden atanamaz.

@No__t_0 bildiri, `using` bloğunda bir özel durum gerçekleşse bile <xref:System.IDisposable.Dispose%2A> çağırılmasını sağlar. Nesneyi `try` bloğunun içine yerleştirerek ve sonra <xref:System.IDisposable.Dispose%2A> bir `finally` bloğunda çağırarak aynı sonucu elde edebilirsiniz; Aslında `using` deyimin derleyici tarafından çevrilme yöntemi budur. Kod örneği, derleme zamanında aşağıdaki koda genişletilir (nesne için sınırlı kapsam oluşturmak için ek küme ayraçları aklınızda):

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

Yeni `using` deyimin sözdizimi, çok benzer bir koda çevrilir. @No__t_0 bloğu, değişkenin bildirildiği yerde açılır. @No__t_0 bloğu, genellikle bir yöntemin sonunda kapsayan bloğun yakın bir tarafında eklenir.

@No__t_0 - `finally` ifadesiyle ilgili daha fazla bilgi için, [try-finally](try-finally.md) konusuna bakın.

Aşağıdaki örnekte gösterildiği gibi, bir türün birden çok örneği `using` bildiriminde bildirilebilecek:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

Aynı türde birden çok bildirimi, C# 8 ' in yanı sıra sunulan yeni sözdizimini kullanarak birleştirebilirsiniz. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

Kaynak nesnesini örnekleyebilirsiniz ve sonra değişkeni `using` ifadesine geçirebilirsiniz, ancak bu en iyi yöntem değildir. Bu durumda, denetim `using` bloğundan ayrıldıktan sonra nesne kapsamda kalır, büyük olasılıkla yönetilmeyen kaynaklarına erişemez. Diğer bir deyişle, artık tam olarak başlatılamaz. Nesneyi `using` bloğunun dışında kullanmaya çalışırsanız, bir özel durumun bir istisna olmasına neden olur. Bu nedenle, `using` deyimindeki nesnenin örneğini oluşturmak ve kapsamını `using` bloğu ile sınırlandırmak genellikle daha iyidir.

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

@No__t_0 nesnelerini elden atma hakkında daha fazla bilgi için, bkz. [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminde](../language-specification/index.md) [using ifadesine](~/_csharplang/spec/statements.md#the-using-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [using Yönergesi](using-directive.md)
- [Atık Toplama](../../../standard/garbage-collection/index.md)
- [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md)
- [IDisposable arabirimi](xref:System.IDisposable)
- [8,0 içinde C# using deyimleri](~/_csharplang/proposals/csharp-8.0/using.md)
