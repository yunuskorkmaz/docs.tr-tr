---
title: Dil özellikleri ve kitaplık türleri arasındaki ilişki | Microsoft Dokümanlar
description: Dil özellikleri genellikle uygulama için kitaplık türlerine dayanır. Bu ilişkiyi anlayın.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61706032"
---
# <a name="relationships-between-language-features-and-library-types"></a>Dil özellikleri ve kitaplık türleri arasındaki ilişkiler

C# dil tanımı, belirli türleri ve bu türlerde belirli erişilebilir üyeleriçin standart bir kitaplık gerektirir. Derleyici, birçok farklı dil özelliği için bu gerekli türleri ve üyeleri kullanan kod oluşturur. Gerektiğinde, bu tür veya üyelerin henüz dağıtılmayan ortamlar için kod yazarken dilin yeni sürümleri için gereken türleri içeren NuGet paketleri vardır.

Standart kitaplık işlevine olan bu bağımlılık, ilk sürümünden beri C# dilinin bir parçası olmuştur. Bu sürümde, örnekler şunlardır:

* <xref:System.Exception>- oluşturulan tüm derleyici özel durumlar için kullanılır.
* <xref:System.String>- C# `string` türü <xref:System.String>.
* <xref:System.Int32>- eşanlamlı `int`.

Bu ilk sürümü basitti: derleyici ve standart kütüphane birlikte sevk ve her biri sadece bir sürümü vardı.

C# sonraki sürümleri bazen bağımlılıklara yeni türler veya üyeler ekledi. Örnekler şunlardır: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> ve <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 [tuples](../tuples.md) dil <xref:System.ValueTuple> özelliğini uygulamak için bir bağımlılık ekleyerek bu devam ediyor.

Dil tasarımı ekibi, uyumlu bir standart kitaplıkta gerekli olan türlerin ve üyelerin yüzey alanını en aza indirmek için çalışır. Bu hedef, yeni kütüphane özelliklerinin dile sorunsuz bir şekilde dahil edildiği temiz bir tasarıma karşı dengelenir. C#'nin gelecekteki sürümlerinde standart bir kitaplıkta yeni türler ve üyeler gerektiren yeni özellikler olacaktır. Bu bağımlılıkları işinizde nasıl yönetebileceğinizi anlamak önemlidir.

## <a name="managing-your-dependencies"></a>Bağımlılıklarınızı yönetme

C# derleyici araçları artık desteklenen platformlarda .NET kitaplıklarının serbest bırakma döngüsünden ayrılmıştır. Aslında, farklı .NET kitaplıkları farklı sürüm döngüleri vardır: .NET Framework Windows Update olarak yayımlanan, .NET Core ayrı bir programda gemi ve kütüphane güncellemeleri Xamarin sürümleri her hedef platform için Xamarin araçları ile gemi.

Çoğu zaman, bu değişiklikleri fark etmezsiniz. Ancak, bu platformdaki .NET kitaplıklarında henüz olmayan özellikler gerektiren dilin daha yeni bir sürümüyle çalışırken, bu yeni türleri sağlamak için NuGet paketlerine başvurursunuz.
Uygulamanızın desteklediği platformlar yeni çerçeve yüklemeleriyle güncelleştirildikçe, ek başvuruyu kaldırabilirsiniz.

Bu ayrım, ilgili çerçeveye sahip olmayan makineleri hedefliyorsanız bile yeni dil özelliklerini kullanabileceğiniz anlamına gelir.
