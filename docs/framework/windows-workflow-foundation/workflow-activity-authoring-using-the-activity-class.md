---
title: "Etkinlik sınıfını kullanarak etkinliği iş akışı yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94433d398f662a96bf046603574ad881128a2081
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Etkinlik sınıfını kullanarak etkinliği iş akışı yazma
Kullanarak bir etkinlik oluşturmak için en temel yolu [!INCLUDE[wf](../../../includes/wf-md.md)] içinde [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] öğesinden devralınan bir sınıf oluşturmak için <xref:System.Activities.Activity> işlevselliği birleştirerek özel oluşturan etkinlikler veya etkinliklerden [yerleşik etkinlik kitaplığı ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Bu konuda iki ileti konsola bir etkinlik oluşturma gösterilir.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Etkinlik Tasarımcısı'nı kullanarak bir özel etkinlik oluşturmak için  
  
1.  Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Dosya, yeni, proje'i seçin. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi. Yeni Proje HelloActivity olarak adlandırın.  
  
3.  Yeni Etkinlik açın.  Sürükleme bir <xref:System.Activities.Statements.Sequence> Tasarımcı yüzeyine araç etkinliğinden.  
  
4.  Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> etkinlik. Girin `"Hello World"` (ile tırnak işaretleri) içine **metin** alan.  
  
5.  İkinci bir sürükleyin <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> ilk aşağıda etkinlik. Girin `"Goodbye"` (ile tırnak işaretleri) içine **metin** alan.
