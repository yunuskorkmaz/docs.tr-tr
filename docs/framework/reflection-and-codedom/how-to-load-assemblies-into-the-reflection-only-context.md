---
title: 'Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme'
description: .NET 'teki yalnızca yansıma bağlamına derlemelerin nasıl yükleneceğini gösteren bir örnek görüntüleyin. Diğer platformlar veya .NET sürümleri için derlenen derlemeleri inceleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
ms.openlocfilehash: 92f847f6c61ba39bf8621af6080baccfdabe514a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865079"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme

Yalnızca yansıma yük bağlamı, diğer platformlar veya .NET Framework diğer sürümleri için derlenen derlemeleri incelemenizi sağlar. Bu içeriğe yüklenen kod yalnızca incelenebilir; yürütülemiyor. Bu, oluşturucular yürütülemediğinden nesnelerin oluşturulamadığını gösterir. Kod yürütülemediğinden, bağımlılıklar otomatik olarak yüklenmez. Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemeniz gerekir.

## <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Bir derlemeyi yalnızca yansıma yükleme bağlamına yüklemek için

1. Kendi <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> görünen adı verilen derlemeyi yüklemek için yöntem aşırı yüklemesini veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> kendi yolu verilen derlemeyi yüklemek için yöntemini kullanın. Derleme bir ikili görüntüdür, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> yöntem aşırı yüklemesini kullanın.

    > [!NOTE]
    > mscorlib.dll sürümünü yürütme bağlamdaki sürümden farklı bir .NET Framework sürümüne yüklemek için yalnızca yansıma bağlamını kullanamazsınız.

2. Derlemenin bağımlılıkları varsa, <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> yöntemi onları yüklemez. Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemeniz gerekir.

3. Derlemenin özelliğini kullanarak bir derlemenin yalnızca yansıma bağlamına yüklenip yüklenmediğini belirleme <xref:System.Reflection.Assembly.ReflectionOnly%2A> .

4. Derleme için derlemeye veya derlemedeki türlere öznitelikler uygulanmışsa, <xref:System.Reflection.CustomAttributeData> yalnızca yansıma bağlamındaki kodu yürütmek için girişimde bulunmadığından emin olmak için sınıfını kullanarak bu öznitelikleri inceleyin. <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> <xref:System.Reflection.CustomAttributeData> Bir derlemeye, üyeye, modüle veya parametreye uygulanan öznitelikleri temsil eden nesneleri almak için yönteminin uygun aşırı yüklemesini kullanın.

    > [!NOTE]
    > Derlemeye veya içeriğine uygulanan öznitelikler derlemede tanımlanabilir veya yalnızca yansıma bağlamına yüklenmiş başka bir derlemede tanımlanabilir. Özniteliklerin tanımlandığı yerde önceden söylemek için bir yol yoktur.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, yalnızca yansıma bağlamına yüklenmiş bir derlemeye uygulanan özniteliklerin nasıl inceleneceğini göstermektedir.

Kod örneği, iki Oluşturucusu ve bir özelliği olan özel bir özniteliği tanımlar. Özniteliği derlemeye, derlemede tanımlanan bir türe, türünün bir yöntemine ve yönteminin parametresine uygulanır,. Yürütüldüğünde, derleme kendisini yalnızca yansıma bağlamına yükler ve buna uygulanan özel öznitelikler ve içerdiği türler ve üyelere ilişkin bilgileri görüntüler.

> [!NOTE]
> Kod örneğini basitleştirmek için, derleme kendisini yükler ve inceler. Normalde, hem yürütme bağlamına hem de yalnızca yansıma bağlamına yüklenmiş aynı derlemeyi bulmayı beklemez.

[!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
[!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
[!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
