---
title: "Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ded5d11c9a9f93848e17c372e961f9f6a3b4226
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama
Aşağıdaki kod örneğinde nasıl uygulanacağını gösterilen <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygular. Uygulandığında, arabirim ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerini iletişim kurar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: PropertyNameChanged Desenini Uygulama](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [Windows Forms Veri Bağlamada Bildirimi Değiştirme](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
