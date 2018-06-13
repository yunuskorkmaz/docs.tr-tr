---
title: Dil özellikleri ve kitaplık türleri arasındaki ilişkiyi | Microsoft Docs
description: Dil özellikleri genellikle uygulama kitaplığı türlerinde kullanır. Bu ilişki anlayın.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360089"
---
# <a name="relationships-between-language-features-and-library-types"></a>Dil özellikleri ve kitaplık türleri arasındaki ilişkileri

C# dili tanımı belirli türleri ve belirli erişilebilir üyeleri bu türlerine sahip bir standart kitaplığı gerektirir. Derleyici bu gerekli türleri ve üyeleri için birçok farklı dil özelliklerini kullanan kodu oluşturur. Gerektiğinde, burada bu türler veya üyeler henüz dağıtılmamış ortamlar için kodu yazarken dil daha yeni sürümleri için gereken türler içeren NuGet paketleri vardır.

Bu bağımlılık standart kitaplığı işlevselliği, ilk sürümünden bu yana C# dili parçası olmuştur. Bu sürümde, dahil edilen örnekler:

* <xref:System.Exception> -Tüm derleyici oluşturulan özel durumlar için kullanılır.
* <xref:System.String> -C# `string` türüdür eşanlamlısı <xref:System.String>.
* <xref:System.Int32> -, eş anlamlı `int`.

Bu ilk sürüm basit: derleyicisi ve standart kitaplığı sevk birlikte ve her yalnızca bir sürümü vardı.

C# ' ın sonraki sürümleri bazen yeni türleri veya üyeleri için bağımlılıkları eklediniz. Örnekler: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> ve <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 devam bu bağımlılık ekleyerek <xref:System.ValueTuple> uygulamak için [diziler](../tuples.md) dil özelliği.

Dil Tasarım ekibi, türleri ve uyumlu bir standart Kitaplığı'nda gerekli üyeleri yüzey alanını en aza indirmek için çalışır. Bu hedefe burada yeni kitaplık özellikleri diline sorunsuz bir şekilde eklenen temiz bir tasarıma karşı dengelenir. Yeni türleri gerektiren gelecekteki sürümlerinde C# yeni özellikler ve standart kitaplığı üyeleri olacaktır. Bu bağımlılıklar çalışmanızı yönetme anlamak önemlidir.

## <a name="managing-your-dependencies"></a>Bağımlılıklarınız yönetme

C# Derleyici araçları şimdi .NET kitaplıklarına yayın döngüsü desteklenen platformlarda gelen birbirinden ayrılır. Aslında, farklı bir sürüm döngüleri farklı .NET kitaplıklarına olan: .NET Framework Windows üzerinde bir Windows Update ile serbest bırakıldı, .NET Core gelir ayrı bir zamanlama ve her hedef platformu için Xamarin araçlarıyla Kitaplığı güncelleştirmeleri sevk Xamarin sürümleri.

Çoğu zaman, bu değişiklikler fark olmaz. Ancak, bu platformda daha yeni bir sürümüyle özelliklerin gerekli olmayan dil henüz .NET kitaplıklarına çalışırken bu yeni türleri sağlamak için NuGet paketlerini başvuru.
Uygulama destekler, yeni framework yüklemeleriyle güncelleştirilir platformları ek başvuru kaldırabilirsiniz.

Bu ayrım bile karşılık gelen framework olmayabilir makineler hedeflerken yeni dil özellikleri kullanabileceğiniz anlamına gelir.
