---
title: Etkinlik sınıfını kullanarak iş akışı etkinliği yazma
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: abdabc46aa54e19d5a04c5b34d6d2b9be07488d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711869"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Etkinlik sınıfını kullanarak iş akışı etkinliği yazma
Windows Workflow Foundation (WF) kullanarak bir etkinlik oluşturmak için en temel yolu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] öğesinden devralınan bir sınıf oluşturmak <xref:System.Activities.Activity> işlevselliği birleştirerek özel oluşturan etkinlikler veya etkinlikten [yerleşik Etkinlik Kitaplığı](net-framework-4-5-built-in-activity-library.md). Bu konu, iki ileti konsola bir etkinlik oluşturma işlemini gösterir.

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Etkinlik Tasarımcısı'nı kullanarak özel bir etkinlik oluşturmak için

1.  Visual Studio 2012'yi açın.

2.  Dosya, yeni, proje'i seçin. Seçin **Workflow 4.0** altında **Visual C#** içinde **proje türleri** penceresi ve select **v2010** düğümü. Seçin **etkinlik Kitaplığı** içinde **şablonları** penceresi. Yeni Proje HelloActivity adı.

3.  Yeni Etkinlik açın.  Sürükleme bir <xref:System.Activities.Statements.Sequence> Tasarımcı yüzeyine araç kutusundan.

4.  Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> etkinlik. Girin `"Hello World"` (teklifler ile) içine **metin** alan.

5.  İkinci sürükleyin <xref:System.Activities.Statements.WriteLine> etkinliğini <xref:System.Activities.Statements.Sequence> ilki aşağıda bir etkinlik. Girin `"Goodbye"` (teklifler ile) içine **metin** alan.
