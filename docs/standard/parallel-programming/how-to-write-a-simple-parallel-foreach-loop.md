---
title: Parallel.ForEach kullanarak basit bir paralel programı yazma
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 599432af178031a85dea4155a8fd2923f879a600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427363"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Nasıl yapılır: Basit bir Parallel.ForEach döngüsü yazma

Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> veri paralelliği herhangi birini etkinleştirmek için döngü <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> veri kaynağı.

> [!NOTE]
> Bu belgede lambda ifadeleri PLINQ'te temsilciler tanımlamak için kullanılır. İle lambda ifadelerine aşina değilseniz C# veya Visual Basic, bkz: [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Örnek

Bu örnekte birkaç .jpg dosya olduğunu varsayar bir *C:\Users\Public\Pictures\Sample resimleri* klasörü ve yeni bir alt klasör oluşturur *değiştirilen*. Örneği çalıştırdığınızda, her bir .jpg resim, döndürür. *örnek resimler* ve kaydeder *değiştirilen*. İki yolu gerektiği gibi değiştirebilirsiniz.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngü çalışır gibi bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü. Döngü, kaynak koleksiyonu bölümler ve sistem ortamına bağlı olarak, birden çok iş parçacığı üzerinde çalışma zamanlar. Daha fazla işlemci sistem üzerinde paralel yöntemi daha hızlı çalışır. Bazı kaynak koleksiyonları için hızlı, kaynak ve döngü gerçekleştiren iş türünü boyutuna bağlı olarak sıralı bir döngü olabilir. Performans hakkında daha fazla bilgi için bkz: [veri ve görev paralelliği olası Tuzaklar](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)

Paralel döngüler hakkında daha fazla bilgi için bkz: [nasıl yapılır: Basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Kullanılacak <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> kullanabileceğiniz bir genel olmayan koleksiyonu ile <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi genel bir koleksiyon için koleksiyon dönüştürmek için:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Paralel LINQ (PLINQ) işlenmesini paralel hale getirmek için de kullanabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veri kaynakları. PLINQ, döngü davranışı ifade etmek için bildirim temelli bir sorgu söz dizimi kullanmanıza olanak sağlar. Daha fazla bilgi için [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Derleme ve kod çalıştırma

Kodu bir konsol uygulaması için .NET Framework veya .NET Core konsol uygulaması olarak derleyebilirsiniz.

Visual Studio'da Visual Basic vardır ve C# Windows Masaüstü ve .NET Core konsol uygulaması şablonları.

Komut satırından .NET Core ve CLI araçlarını da kullanabilirsiniz (örneğin, `dotnet new console` veya `dotnet new console -lang vb`), veya dosyayı oluşturmak ve komut satırı derleyicisi için bir .NET Framework uygulamasını kullanın.

Bir .NET Core projesi için başvuru gerekir **System.Drawing.Common** NuGet paketi. Visual Studio'da NuGet Paket Yöneticisi paketini yüklemek için kullanın. Alternatif olarak, pakete bir başvuru ekleyebilirsiniz, \*.csproj veya \*.vbproj dosyası:
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Komut satırından .NET Core konsol uygulaması çalıştırmak için kullanın `dotnet run` uygulamanızı içeren klasörden.

Konsol uygulamanızı Visual Studio'dan çalıştırmak için basın **F5**.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
