---
title: Windows Workflow Foundation’da kullanım dışı türler
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: c8325e60d708b53e1701a980355d5d2bf20e8a4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644964"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation’da kullanım dışı türler
.NET 4'te iş akışı takımın tüm yeni bir iş akışı altyapısında yayımlanan <xref:System.Activities> ad alanı. .NET 4.5 Beta sürümünde biz "WF 3" içindeki türlerin çoğu işaretleme <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, ve <xref:System.Workflow.Runtime> artık kullanılmıyor olarak ad alanları.  
  
## <a name="obsolete-namespaces-and-tools"></a>Artık kullanılmayan ad alanları ve araçları  
 Aşağıdaki derlemelerini kullanım dışı bırakılacak bir veya daha fazla genel tür vardır:  
  
- System.Workflow.Activities.dll  
  
- System.Workflow.ComponentModel.dll  
  
- System.Workflow.Runtime.dll  
  
- System.WorkflowServices.dll  
  
- Microsoft.Workflow.DebugController.dll  
  
- Microsoft.Workflow.Compiler.exe  
  
- Wfc.exe  
  
 Sonuç olarak, kullanım dışı WF 3 API'lerini kullanan müşteriler, derleme uyarıları aşağıdakine benzer bir ileti ile karşılaşırsınız:  
  
 **Uyarı BC40000: X artık kullanılmıyor: WF 3 türleri kullanım dışı bırakılmıştır. Bunun yerine WF 4 kullanın.** Gelecek sürümlerden birinde .NET Framework türleri kaldıracağız, ancak henüz bu zaman çerçevesi (değil, 4.5) belirledik değil. Bu geçerli adımı bizim yönü müşterilerimiz için iletişim ve yeni WF4 modeline taşıma zamanı bolca izin olanak sağlıyor. Biz, altında bu WF 3 türlerini destekleyecek şekilde devam eder [Microsoft destek yaşam döngüsü ilkesi](https://aka.ms/MicrosoftSupportLifecycle). Var olan WF3 uygulamaları sorun, .NET 4.5 üzerinde çalışır ve Visual Studio 2012, yeni ve mevcut WF3 tabanlı çözümler destekleyecektir.  
  
 Kuralları ilgili türlerinde <xref:System.Workflow.Activities.Rules> değiştirme WF 4.5 içinde sahip, ad alanı değil kaldırılmıştır.  
  
 WF 4 uygulamalarını geçirmek isteyen müşteriler, Yardım'da bulacaksınız [iş akışı 4 geçiş kılavuzuna](migration-guidance.md).
