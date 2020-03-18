---
title: 'Nasıl yapılsın: Montajları yükleme ve boşaltma'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155782"
---
# <a name="how-to-load-and-unload-assemblies"></a>Nasıl yapılsın: Montajları yükleme ve boşaltma
Programınız tarafından başvurulan derlemeler ortak dil çalışma süresi tarafından otomatik olarak yüklenir, ancak belirli derlemeleri geçerli uygulama etki alanına dinamik olarak yüklemek de mümkündür. Daha fazla bilgi için [bkz: Derlemeleri bir uygulama etki alanına yükleyin.](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

.NET Framework'de, onu içeren tüm uygulama etki alanlarını boşaltmadan tek bir derlemeyi boşaltmanın bir yolu yoktur. Derleme kapsam dışına çıksa bile, gerçek derleme dosyası, onu içeren tüm uygulama etki alanları kaldırılıncaya kadar yüklenmiş olarak kalır. .NET <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> Core'da, sınıf derlemelerin boşaltılmasını işler. Daha fazla bilgi için [,.NET Core'da derleme yüklenebilirliğinin nasıl kullanılacağı ve hata ayıklanabilirliğinin nasıl kullanılacağına](unloadability.md)bakın.

## <a name="load-and-unload-assemblies"></a>Bütünleştirilmiş kod yükleme ve yüklemelerini kaldırma

Bir derlemeyi uygulama etki alanına yüklemek için, sınıflarda <xref:System.AppDomain> bulunan <xref:System.Reflection.Assembly>birkaç yükleme yönteminden birini kullanın ve. Daha fazla bilgi için [bkz: Derlemeleri bir uygulama etki alanına yükleyin.](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md) .NET Core'un yalnızca tek bir uygulama etki alanını desteklediğini unutmayın.

.NET Framework'deki bir derlemeyi boşaltmak için, derlemeyi içeren tüm uygulama etki alanlarını boşaltmanız gerekir. Bir uygulama etki alanını boşaltmak için <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi kullanın. Daha fazla bilgi için [bkz: Uygulama etki alanını boşaltın.](../../framework/app-domains/how-to-unload-an-application-domain.md)

Bir .NET Framework uygulamasında ki bazı derlemeleri değil, diğerlerini boşaltmak istiyorsanız, yeni bir uygulama etki alanı oluşturmayı, kodu bu etki alanının içinde yürütmeyi ve ardından bu uygulama etki alanını boşaltmayı düşünün. Daha fazla bilgi için [bkz: Uygulama etki alanını boşaltın.](../../framework/app-domains/how-to-unload-an-application-domain.md)  

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Nasıl yapilir: Derlemeleri bir uygulama etki alanına yükleme](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
