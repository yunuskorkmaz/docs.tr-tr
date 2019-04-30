---
title: Dil özellikleri ve kitaplık türleri arasındaki ilişkiyi | Microsoft Docs
description: Dil özellikleri kitaplık türleri için uygulama genellikle dayanır. Bu ilişkiyi anlayın.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706032"
---
# <a name="relationships-between-language-features-and-library-types"></a>Dil özellikleri ve kitaplık türleri arasındaki ilişkileri

C# Belirli türlerini ve belirli erişilebilir üyeler üzerinde bu türleri için standart bir kitaplığı dil tanımı gerektirir. Derleyici için birçok farklı dil özelliklerini bu gerekli türleri ve üyeleri kullanan kod oluşturur. Gerektiğinde, burada bu tür veya üyeler henüz dağıtılmamış ortamları için kod yazma, dil daha yeni sürümleri için gerekli türleri içeren NuGet paketleri vardır.

Bu bağımlılık standart kitaplığı işlevlerini bir parçası olmuştur C# ilk sürümünden bu yana dili. Bu sürümde, dahil edilen örnekler:

* <xref:System.Exception> -Tüm derleyicinin ürettiği özel durumlar için kullanılır.
* <xref:System.String> - C# `string` türüdür ilişkin bir eşanlam <xref:System.String>.
* <xref:System.Int32> -, eş anlamlı `int`.

Bu ilk sürüm basit: derleyici ve standart kitaplık birlikte birlikte ve her yalnızca bir sürümü vardı.

Sonraki sürümlerde C# bazen yeni türleri veya üyeleri için bağımlılıklar ekledik. Örnekler: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> ve <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C#7.0 devam bu bir bağımlılık ekleyerek <xref:System.ValueTuple> uygulamak için [diziler](../tuples.md) dil özelliğidir.

Dil Tasarım ekibi, türler ve üyeler uyumlu standart kitaplığa gerekli'nın yüzey alanını en aza indirmek için çalışır. Bu hedefe burada yeni kitaplık özellikleri diline sorunsuz bir şekilde eklenen temiz bir tasarıma karşı dengelenir. Gelecekteki sürümlerinde yeni özellikler olacaktır C# yeni türler ve üyeler standart Kitaplığı'nda gerektirir. Bu bağımlılıkları çalışmanızı yönetmek nasıl anlamak önemlidir.

## <a name="managing-your-dependencies"></a>Bağımlılıklarınızı yönetme

C#derleme araçları artık .NET kitaplıklarına desteklenen platformlarda sürüm döngüsü'nden birbirinden ayrılmıştır. Aslında, farklı .NET kitaplıkları farklı yayın döngülerine sahiptir: .NET Core birlikte gelen ayrı bir zamanlamaya ve kitaplık güncelleştirmeleri sevk her hedef platform için Xamarin araçları ile Xamarin sürümleri, Windows üzerinde .NET Framework, bir Windows güncelleştirmesi yayımlanır.

Çoğu zaman, bu değişiklikler fark yoktur. Ancak, daha yeni bir sürümüyle .NET kitaplıkları gerektiren özellikleri olmayan dil henüz bu platform üzerinde çalışırken, bu yeni türler sağlamak için NuGet paketlerini başvuru.
Uygulamanızın desteklediği yeni framework yüklemeleri ile güncelleştirilir platformu olarak ek başvuru kaldırabilirsiniz.

Bu ayrım bile karşılık gelen framework olmayabilir makineler hedeflenirken yeni dil özellikleri kullanabileceğiniz anlamına gelir.
