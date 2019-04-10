---
title: 'Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225605"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama
Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygulayın. Arabirim uygulandığında, ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerinin iletişim kurar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: PropertyNameChanged Desenini Uygulama](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme](./controls/raise-change-notifications--bindingsource.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
