---
title: Dil özellikleri ve kitaplık türleri arasındaki ilişki | Microsoft Docs
description: Dil özellikleri genellikle uygulama için kitaplık türlerine bağlıdır. İlişkiyi anlayın.
ms.date: 07/20/2017
ms.openlocfilehash: abf15385da3756c35db2df822cc2e11e9edf5758
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174107"
---
# <a name="relationships-between-language-features-and-library-types"></a>Dil özellikleri ve kitaplık türleri arasındaki ilişkiler

C# dil tanımı, standart bir kitaplığın belirli türlere ve bu türlerde bazı erişilebilir üyelere sahip olmasını gerektirir. Derleyici, birçok farklı dil özelliği için bu gerekli türleri ve üyeleri kullanan kodu oluşturur. Gerektiğinde, bu türlerin veya üyelerin henüz dağıtılmadığı ortamlar için kod yazarken dilin daha yeni sürümleri için gerekli olan türleri içeren NuGet paketleri vardır.

Bu standart kitaplık işlevine bağımlılık, ilk sürümü bu yana C# dilinin bir parçası. Bu sürümde, şunlar dahildir:

* <xref:System.Exception>-Derleyicinin ürettiği tüm özel durumlar için kullanılır.
* <xref:System.String>-C# `string` türü için bir eş anlamlı <xref:System.String> .
* <xref:System.Int32>-eşanlamlısı `int` .

Bu ilk sürüm basittir: derleyici ve standart kitaplık birlikte sevk edildi ve her birinin yalnızca bir sürümü vardı.

Sonraki C# sürümleri, bazı durumlarda bağımlılıklara yeni türler veya Üyeler eklemiştir. Örnekler şunlardır: <xref:System.Runtime.CompilerServices.INotifyCompletion> , <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> ve <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute> . C# 7,0 <xref:System.ValueTuple> , [tanımlama](../language-reference/builtin-types/value-tuples.md) grubu dili özelliğini uygulamak için bir bağımlılık ekleyerek bunu devam ettirir.

Dil tasarımı ekibi, uyumlu bir standart kitaplıkta gerekli olan türlerin ve üyelerin yüzey alanını en aza indirmek için işe yarar. Bu hedef, yeni kitaplık özelliklerinin dile sorunsuz bir şekilde dahil olduğu temiz bir tasarıma karşı dengelenir. Yeni türler ve bir standart kitaplıkta üye gerektiren sonraki C# sürümlerinde yeni özellikler olacaktır. Bu bağımlılıkların çalışmalarda nasıl yönetileceğini anlamak önemlidir.

## <a name="managing-your-dependencies"></a>Bağımlılıklarınızı yönetme

C# derleyici araçları artık desteklenen platformlarda .NET kitaplıklarının yayın döngüsünden ayrılır. Aslında, farklı .NET kitaplıklarında farklı sürüm döngüleri vardır: Windows 'daki .NET Framework Windows Update olarak yayımlanmıştır, .NET Core ayrı bir zamanlamaya göre gelir ve kitaplık güncelleştirmelerinin Xamarin sürümleri her hedef platform için Xamarin araçlarıyla birlikte gönderilir.

Büyük bir süre içinde, bu değişiklikleri fark edeceksiniz. Ancak, bu platformun henüz .NET kitaplıklarında bulunmayan özellikleri gerektiren dilin daha yeni bir sürümüyle çalışırken, bu yeni türleri sağlamak için NuGet paketlerine başvurabileceksiniz.
Uygulamanızın desteklediği platformlar yeni çerçeve yüklemeleri ile güncelleştirilerek, ek başvuruyu kaldırabilirsiniz.

Bu ayrım, karşılık gelen çerçeveye sahip olmayan makineleri hedeflerken bile yeni dil özelliklerini kullanabileceğiniz anlamına gelir.
