---
title: 'Nasıl yapılır: Derlemeleri yükle ve Kaldır'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973203"
---
# <a name="how-to-load-and-unload-assemblies"></a>Nasıl yapılır: Derlemeleri yükle ve Kaldır
Programınızın başvurduğu derlemeler, ortak dil çalışma zamanı tarafından otomatik olarak yüklenir, ancak belirli derlemeleri geçerli uygulama etki alanına dinamik olarak yüklemek de mümkündür. Daha fazla bilgi için [nasıl yapılır: Derlemeleri bir uygulama etki alanına](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)yükleyin.

.NET Framework, kendisini içeren tüm uygulama etki alanlarını kaldırmadan tek bir derlemeyi kaldırma yöntemi yoktur. Derleme kapsam dışına çıksa bile, kendisini içeren tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklenmeyecektir. .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> 'da sınıf, derlemelerin kaldırılmasını işler. Daha fazla bilgi için bkz. [.NET Core 'da derleme geri kullanımını kullanma ve hata ayıklama](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Derlemeleri yükle ve Kaldır

Bir derlemeyi uygulama etki alanına yüklemek için sınıflarda <xref:System.AppDomain> <xref:System.Reflection.Assembly>bulunan çeşitli yükleme yöntemlerinden birini kullanın. Daha fazla bilgi için [nasıl yapılır: Derlemeleri bir uygulama etki alanına](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)yükleyin. .NET Core 'un yalnızca tek bir uygulama etki alanını desteklediğini unutmayın. 

.NET Framework bir derlemeyi kaldırmak için, kendisini içeren tüm uygulama etki alanlarını kaldırmanız gerekir. Bir uygulama etki alanını kaldırmak için <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemini kullanın. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanını](../../framework/app-domains/how-to-unload-an-application-domain.md)kaldırın.

Bir .NET Framework uygulamasında bazı derlemeleri kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturmayı, bu etki alanı içinde kodu yürütmeyi ve ardından bu uygulama etki alanını kaldırmayı düşünün. Daha fazla bilgi için [nasıl yapılır: Bir uygulama etki alanını](../../framework/app-domains/how-to-unload-an-application-domain.md)kaldırın.  

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Nasıl yapılır: Derlemeleri bir uygulama etki alanına yükleme](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
