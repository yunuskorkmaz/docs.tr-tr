---
title: 'Nasıl yapılır: .NET standart bir nesne seri hale getirilebilir olup olmadığını belirler'
description: Çalışma zamanında .NET standart bir türü seri olup olmadığını belirlemek gösterilmiştir.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 247eed2e7091930c6bcfaa524296b45350dd6510
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
<xref:System.SerializableAttribute?displayProperty=nameWithType>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
