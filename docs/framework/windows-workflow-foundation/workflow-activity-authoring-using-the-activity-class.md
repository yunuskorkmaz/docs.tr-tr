---
title: Etkinlik sınıfını kullanarak iş akışı etkinliği yazma
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 21f1c8b1249d41029fa7a19360e96ad866c823a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293851"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Etkinlik sınıfını kullanarak iş akışı etkinliği yazma

' De Windows Workflow Foundation (WF) kullanarak bir etkinlik oluşturmanın en temel yolu, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <xref:System.Activities.Activity> [yerleşik etkinlik kitaplığından](net-framework-4-5-built-in-activity-library.md)özel etkinlikleri veya etkinlikleri derleyerek Bu işlevden devralan bir sınıf oluşturmaktır. Bu konuda, konsola iki ileti yazan bir etkinliğin nasıl oluşturulacağı gösterilmektedir.

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Etkinlik tasarımcısını kullanarak özel bir etkinlik oluşturmak için

1. Visual Studio 2012 ' i açın.

2. Dosya, yeni, proje ' yi seçin. **Proje türleri** penceresinde **Visual C#** altında **iş akışı 4,0** ' i seçin ve **v2010** düğümünü seçin. **Şablonlar** penceresinde **etkinlik kitaplığı** ' nı seçin. Yeni proje Merhaba etkinliğini adlandırın.

3. Yeni etkinliği açın.  <xref:System.Activities.Statements.Sequence>Araç kutusundan bir etkinliği tasarımcı yüzeyine sürükleyin.

4. Etkinliği etkinliğe sürükleyin <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Sequence> . `"Hello World"` **Metin** alanına (tırnak işareti ile) girin.

5. İkinci bir <xref:System.Activities.Statements.WriteLine> etkinliği <xref:System.Activities.Statements.Sequence> , birincinin altında, etkinliğe sürükleyin. `"Goodbye"` **Metin** alanına (tırnak işareti ile) girin.
