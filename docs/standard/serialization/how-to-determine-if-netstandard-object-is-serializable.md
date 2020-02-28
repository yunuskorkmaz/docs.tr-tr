---
title: .NET Standard nesnenin seri hale getirilebilir olup olmadığını belirleme
description: .NET Standard türünün çalışma zamanında seri hale getirilebilir olup olmadığını nasıl belirleyecağınızı gösterir.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: 4037dee36aeb619eb2757016904fd877158e57cf
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159903"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>.NET Standard nesnenin seri hale getirilebilir olup olmadığını belirleme

.NET Standard, standart bu sürümü ile uyumlu olan belirli .NET uygulamalarında bulunması gereken türleri ve üyeleri tanımlayan bir belirtimdir. Ancak .NET Standard, bir türün seri hale getirilebilir olup olmadığını tanımlamaz. .NET Standard kitaplığı 'nda tanımlanan türler <xref:System.SerializableAttribute> özniteliğiyle işaretlenmez. Bunun yerine, .NET Framework ve .NET Core gibi belirli .NET uygulamaları, belirli bir türün serileştirilebilir olup olmadığını belirlemekte ücretsizdir.

.NET Standard hedefleyen bir kitaplık geliştirdiyseniz, kitaplığınız .NET Standard destekleyen herhangi bir .NET uygulaması tarafından tüketilebilir. Bu, belirli bir türün serileştirilebilir olup olmadığını önceden belirleyemeyeceğiniz anlamına gelir. çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz.

Nesnenin türünü temsil eden bir <xref:System.Type> nesnesinin <xref:System.Type.IsSerializable> özelliğinin değerini alarak, bir nesnenin çalışma zamanında seri hale getirilebilir olup olmadığını belirleyebilirsiniz. Aşağıdaki örnek bir uygulama sağlar. Herhangi bir <xref:System.Object> örneğinin seri hale getirilemeyeceğini belirten bir `IsSerializable(Object)` uzantısı yöntemi tanımlar.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Daha sonra aşağıdaki örnekte gösterildiği gibi, geçerli .NET uygulamasında seri hale getirilebilir ve seri durumdan çıkarılamayacağını öğrenmek için yöntemine herhangi bir nesne geçirebilirsiniz:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- [İkili serileştirme](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
