---
title: Etkinlik sınıfını kullanarak etkinliği iş akışı yazma
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 040fe777e332efdfb296e6fb6565935f466ded71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Etkinlik sınıfını kullanarak etkinliği iş akışı yazma
Windows Workflow Foundation (WF) kullanan bir etkinlik oluşturmak için en temel yolu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] öğesinden devralınan bir sınıf oluşturmak için <xref:System.Activities.Activity> işlevselliği birleştirerek özel oluşturan etkinlikler veya etkinliklerden [yerleşik Etkinlik Kitaplığı](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Bu konuda iki ileti konsola bir etkinlik oluşturma gösterilir.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Etkinlik Tasarımcısı'nı kullanarak bir özel etkinlik oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Dosya, yeni, proje'i seçin. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi. Yeni Proje HelloActivity olarak adlandırın.  
  
3.  Yeni Etkinlik açın.  Sürükleme bir <xref:System.Activities.Statements.Sequence> Tasarımcı yüzeyine araç etkinliğinden.  
  
4.  Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> etkinlik. Girin `"Hello World"` (ile tırnak işaretleri) içine **metin** alan.  
  
5.  İkinci bir sürükleyin <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> ilk aşağıda etkinlik. Girin `"Goodbye"` (ile tırnak işaretleri) içine **metin** alan.
