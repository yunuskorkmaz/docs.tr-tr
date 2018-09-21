---
title: .NET Standard nesnesinin serileştirilebilir olup olmadığını belirleme
description: Çalışma zamanında bir .NET Standard türü seri olup olmadığını belirlemek nasıl gösterir.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525493"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>.NET Standard nesnesinin serileştirilebilir olup olmadığını belirleme

.NET Standard türleri ve bu standart sürümüne uygun belirli .NET uygulamaları üzerinde bulunması gereken üyeleri tanımlayan bir özelliğidir. Ancak, .NET Standard seri hale getirilebilir bir tür olup olmadığını tanımlamaz. .NET Standard Kitaplığı'nda tanımlanan türleri ile işaretlenmemiş <xref:System.SerializableAttribute> özniteliği. Bunun yerine, belirli .NET uygulamaları, .NET Framework ve .NET Core gibi belirli bir tür serileştirilebilir olup olmadığını belirlemek ücretsizdir. 

Hedefleyen .NET Standard kitaplığı geliştirdiyseniz kitaplığınızı .NET Standard destekleyen herhangi bir .NET uygulaması tarafından kullanılır. Başka bir deyişle, önceden belirli bir türü seri hale getirilebilir olduğunu bildiğiniz olamaz; yalnızca, çalışma zamanında serileştirilebilir olup olmadığını belirler.

Bir nesnenin değerini alarak çalışma zamanında serileştirilebilir olup olmadığını belirlemek <xref:System.Type.IsSerializable> özelliği bir <xref:System.Type> nesnenin türünü temsil eden nesne. Aşağıdaki örnek, bir uygulamasını sağlar. Tanımladığı bir `IsSerializable(Object)` gösteren bir genişletme yöntemi olmadığını <xref:System.Object> örneği seri hale getirilemiyor.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Ardından, sıralanabilir ve geçerli .NET uygulaması aşağıdaki örnekte gösterildiği gibi seri durumdan olup olmadığını belirlemek için yöntemin herhangi bir nesne geçirebilirsiniz:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [İkili seri hale getirme](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
