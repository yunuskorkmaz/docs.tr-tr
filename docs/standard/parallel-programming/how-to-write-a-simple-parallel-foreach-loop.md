---
title: Parallel.ForEach kullanarak basit bir paralel program yazın
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 02b94b673dc4468e68a1dadd83aab0e3bfcfaa16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160306"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Nasıl: Basit bir Parallel.ForEach döngüsü yazın

Bu örnek, herhangi <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> <xref:System.Collections.IEnumerable?displayProperty=nameWithType> bir veri kaynağı üzerinde <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri paralelliği etkinleştirmek için bir döngü nasıl kullanılacağını gösterir.

> [!NOTE]
> Bu dokümantasyon PLINQ'daki delegeleri tanımlamak için lambda ifadelerini kullanır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda ifadelerine](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.

## <a name="example"></a>Örnek

Bu örnek, *C:\Users\Public\Pictures\Sample Pictures* klasöründe birkaç .jpg dosyanız olduğunu varsayar ve *Değiştirilen*adlı yeni bir alt klasör oluşturur. Örneği çalıştırdığınızda, *Örnek Resimler'deki* her .jpg görüntüsünü döndürür ve *Değiştirilmiştir.* İki yolu gerektiği gibi değiştirebilirsiniz.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngü döngü <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> gibi çalışır. Döngü, kaynak koleksiyonunu bölümlere ayırır ve çalışmayı sistem ortamına göre birden çok iş parçacığı üzerinde zamanlar. Sistemde ne kadar çok işlemci ne kadar çok çalışırsa, paralel yöntem o kadar hızlı çalışır. Bazı kaynak koleksiyonlarıiçin, kaynağın boyutuna ve döngünün gerçekleştirdiği iş türüne bağlı olarak sıralı bir döngü daha hızlı olabilir. Performans hakkında daha fazla bilgi için veri [ve görev paralellik olası tuzaklar](potential-pitfalls-in-data-and-task-parallelism.md)bakın.

Paralel döngüler hakkında daha fazla bilgi için [bkz: Basit bir Parallel.For döngüsü yazın.](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)

Genel <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> olmayan bir koleksiyonla kullanmak için, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi koleksiyonu genel bir koleksiyona dönüştürmek için uzantı yöntemini kullanabilirsiniz:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Veri kaynaklarının <xref:System.Collections.Generic.IEnumerable%601> işlenmesini paralelleştirmek için Paralel LINQ (PLINQ) de kullanabilirsiniz. PLINQ döngü davranışını ifade etmek için bildirimsel sorgu sözdizimini kullanmanıza olanak tanır. Daha fazla bilgi için [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)bakın.

## <a name="compile-and-run-the-code"></a>Kodu derle ve çalıştır

Kodu .NET Framework için konsol uygulaması olarak veya .NET Core için konsol uygulaması olarak derleyebilirsiniz.

Visual Studio'da Windows Desktop ve .NET Core için Visual Basic ve C# konsol uygulama şablonları vardır.

Komut satırından ,.NET Core CLI komutlarını (örneğin, `dotnet new console` veya) `dotnet new console -lang vb`kullanabilir veya dosyayı oluşturabilir ve .NET Framework uygulaması için komut satırı derleyicisini kullanabilirsiniz.

Bir .NET Core projesi için **System.Drawing.Common** NuGet paketine başvurmanız gerekir. Visual Studio'da paketi yüklemek için NuGet Paket Yöneticisi'ni kullanın. Alternatif olarak, .csproj veya \* \*.vbproj dosyanızdaki pakete bir başvuru ekleyebilirsiniz:

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Komut satırından bir .NET Core konsol `dotnet run` uygulaması çalıştırmak için uygulamanızı içeren klasörden kullanın.

Konsol uygulamanızı Visual Studio'dan çalıştırmak için **F5**tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel programlama](../../../docs/standard/parallel-programming/index.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
