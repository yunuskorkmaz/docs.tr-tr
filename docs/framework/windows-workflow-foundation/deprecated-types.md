---
title: Windows Workflow Foundation kullanım dışı türleri
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 899d21f23c0500a1df01916d1da210b2f9bea95b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Windows Workflow Foundation kullanım dışı türleri
Tüm yeni bir iş akışı altyapısında iş akışı takım .NET 4'te yayımlanan <xref:System.Activities> ad alanı. .NET 4.5 Beta sürümünden biz "WF 3" türlerinde çoğunu işaretleme <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, ve <xref:System.Workflow.Runtime> artık kullanılmayan olarak ad alanları.  
  
## <a name="obsolete-namespaces-and-tools"></a>Artık kullanılmayan ad alanları ve araçları  
 Aşağıdaki derlemeler kullanım dışı kalacaktır bir veya daha fazla genel tür vardır:  
  
-   System.Workflow.Activities.dll  
  
-   System.Workflow.ComponentModel.dll  
  
-   System.Workflow.Runtime.dll  
  
-   System.WorkflowServices.dll  
  
-   Microsoft.Workflow.DebugController.dll  
  
-   Microsoft.Workflow.Compiler.exe  
  
-   WFC.exe  
  
 Sonuç olarak, kullanım dışı WF 3 API'lerini kullanan müşteriler oluşturma uyarıları aşağıdakine benzer bir iletiyle karşılaşırsınız:  
  
 **Uyarı BC40000: X kullanılmıyor: WF 3 türleri dışıdır. Lütfen WF 4 kullanın.** Biz türleri gelecek bir sürümde .NET Framework kaldıracak, ancak henüz o zaman çerçevesinde (değil 4.5) belirledik değil. Geçerli bu adımı bize müşterilerimizin bizim yönüne iletişim kurmasını ve onu bol yeni WF4 modeline taşmanın ne zaman izin verir. Elbette, altında bu WF 3 türlerini desteklemek devam [Microsoft destek yaşam döngüsü ilkesi](http://aka.ms/MicrosoftSupportLifecycle). Varolan WF3 uygulamaları, .NET 4.5, sorun çalışır ve [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] yeni ve mevcut WF3 tabanlı çözümler destekleyecektir.  
  
 Kuralları ilgili türlerinde <xref:System.Workflow.Activities.Rules> yenisini WF 4.5 gerekmez, ad alanı değil kullanımdan kaldırıldı.  
  
 WF 4 uygulamalarını geçirmek isteyen müşteriler, Yardım'da bulacaksınız [iş akışı 4 Geçiş Kılavuzu](migration-guidance.md).
