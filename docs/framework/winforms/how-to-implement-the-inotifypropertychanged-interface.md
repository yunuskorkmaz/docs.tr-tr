---
title: "Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama
Aşağıdaki kod örneğinde nasıl uygulanacağını gösterilen <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygular. Uygulandığında, arabirim ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerini iletişim kurar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: PropertyNameChanged desenini uygulama](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Windows Forms veri bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Windows Forms veri bağlamada bildirimi değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
