---
title: 'Nasıl yapılır: derlemeleri yükleme ve kaldırma'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155782"
---
# <a name="how-to-load-and-unload-assemblies"></a>Nasıl yapılır: derlemeleri yükleme ve kaldırma
Programınızın başvurduğu derlemeler, ortak dil çalışma zamanı tarafından otomatik olarak yüklenir, ancak belirli derlemeleri geçerli uygulama etki alanına dinamik olarak yüklemek de mümkündür. Daha fazla bilgi için bkz. [nasıl yapılır: derlemeleri bir uygulama etki alanına yükleme](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

.NET Framework, kendisini içeren tüm uygulama etki alanlarını kaldırmadan tek bir derlemeyi kaldırma yöntemi yoktur. Derleme kapsam dışına çıksa bile, kendisini içeren tüm uygulama etki alanları kaldırılana kadar gerçek derleme dosyası yüklenmeyecektir. .NET Core 'da <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> sınıfı derlemelerin kaldırılmasını işler. Daha fazla bilgi için bkz. [.NET Core 'da derleme geri kullanımını kullanma ve hata ayıklama](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Bütünleştirilmiş kod yükleme ve yüklemelerini kaldırma

Bir derlemeyi uygulama etki alanına yüklemek için, sınıflarda bulunan çeşitli yükleme yöntemlerinden birini kullanın <xref:System.AppDomain> ve <xref:System.Reflection.Assembly>. Daha fazla bilgi için bkz. [nasıl yapılır: derlemeleri bir uygulama etki alanına yükleme](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). .NET Core 'un yalnızca tek bir uygulama etki alanını desteklediğini unutmayın.

.NET Framework bir derlemeyi kaldırmak için, kendisini içeren tüm uygulama etki alanlarını kaldırmanız gerekir. Bir uygulama etki alanını kaldırmak için <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama etki alanını kaldırma](../../framework/app-domains/how-to-unload-an-application-domain.md).

Bir .NET Framework uygulamasında bazı derlemeleri kaldırmak istiyorsanız, yeni bir uygulama etki alanı oluşturmayı, bu etki alanı içinde kodu yürütmeyi ve ardından bu uygulama etki alanını kaldırmayı düşünün. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama etki alanını kaldırma](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [Nasıl yapılır: bir uygulama etki alanına derlemeler yükleme](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
