---
title: Windows Workflow Foundation’da kullanım dışı türler
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 011f13a56695efdd9e964ef1e6c1099b0acc2710
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713346"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation’da kullanım dışı türler
.NET 4 ' te Iş akışı ekibi, ad alanında yeni bir Iş akışı altyapısı yayımlamıştır <xref:System.Activities> . .NET Framework 4,5 Beta sürümü sayesinde, "WF 3" <xref:System.Workflow.Activities> , ve ad alanlarındaki türlerin çoğunu <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> eski olarak işaretliyoruz.

## <a name="obsolete-namespaces-and-tools"></a>Kullanılmayan ad alanları ve araçları
 Aşağıdaki derlemeler, kullanım dışı bırakılacak bir veya daha fazla ortak türe sahiptir:

- System.Workflow.Activities.dll

- System.Workflow.ComponentModel.dll

- System.Workflow.Runtime.dll

- System.WorkflowServices.dll

- Microsoft.Workflow.DebugController.dll

- Microsoft.Workflow.Compiler.exe

- Wfc.exe

 Sonuç olarak, kullanımdan kaldırılan WF 3 API 'Leri kullanan müşteriler, aşağıdakine benzer bir iletiyle birlikte derleme uyarıları ile karşılaşacaktır:

 **Uyarı BC40000: X artık kullanılmıyor: WF 3 türleri kullanım dışıdır. Lütfen bunun yerine WF 4 kullanın.** Gelecekteki bir sürümdeki .NET Framework türleri kaldıracağız, ancak henüz bu zaman dilimini (4,5 ' de değil) belirliyoruz. Bu geçerli adım, müşterilerimiz için yönümüzü iletmemize ve yeni WF4 modeline geçiş yapmak için yeterince zaman sağlar. Tabii ki, [Microsoft desteği yaşam döngüsü ilkesi](/lifecycle/)altında bu WF 3 türlerini desteklemeye devam edeceğiz. Mevcut WF3 uygulamaları .NET Framework 4,5 ' de sorun olmadan çalışacaktır ve Visual Studio 2012, yeni ve var olan WF3 tabanlı çözümleri destekleyecektir.

 Ad alanındaki kurallarla ilgili türler <xref:System.Workflow.Activities.Rules> , WF 4,5 ' de değişiklik olmayan, kullanım dışı bırakılmış.

 Uygulamalarını WF 4 ' e geçirmek isteyen müşteriler, [Iş akışı 4 geçiş kılavuzunda](migration-guidance.md)yardım bulacaktır.
