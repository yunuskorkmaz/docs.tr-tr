---
title: "Nasıl yapılır: .NET standart bir nesne seri hale getirilebilir olup olmadığını belirler"
description: "Çalışma zamanında .NET standart bir türü seri olup olmadığını belirlemek gösterilmiştir."
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c44e350ad4e561f03bf6c598172058a0a9ca41e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Nasıl yapılır: .NET standart bir nesne seri hale getirilebilir olup olmadığını belirler

.NET standart türleri ve bu standart sürümüne uygun belirli .NET uygulamaları üzerinde mevcut olmalıdır üyeleri tanımlayan bir özelliğidir. Ancak, .NET standart bir türü seri hale getirilebilir olup olmadığını tanımlamaz. .NET standart Kitaplığı'nda tanımlanan türleri ile işaretlenmemiş <xref:System.SerializableAttribute> özniteliği. Bunun yerine, belirli .NET, .NET Framework ve .NET Core gibi belirli bir türü seri hale getirilebilir olup olmadığını belirlemek boş uygulamalarıdır. 

Bir kitaplık hedefleyen .NET standart geliştirdik, kitaplığınızın .NET standardını destekleyen herhangi bir .NET uygulaması tarafından tüketilebilir. Bu, önceden belirli bir türü seri hale getirilebilir olup olmadığını bilemezsiniz olduğunu anlamına gelir; yalnızca, çalışma zamanında seri hale getirilebilir olup olmadığını belirler.

Değerini alarak nesneyi çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz <xref:System.Type.IsSerializable> özelliği bir <xref:System.Type> o nesnenin türünü temsil eden nesne. Aşağıdaki örnek bir uygulama sağlar. Bunu tanımlayan bir `IsSerializable(Object)` gösterir genişletme yöntemi olup <xref:System.Object> örneği hale getirilebilir.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Ardından, herhangi bir nesne, sıralanabilir ve aşağıdaki örnekte gösterildiği gibi geçerli .NET uygulaması seri olup olmadığını belirlemek amacıyla yöntemi geçirebilirsiniz:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a>Ayrıca bkz.

[İkili seri hale getirme](binary-serialization.md)   
<xref:System.SerializableAttribute?displayProperty=fullName>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
