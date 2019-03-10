---
title: 'Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 51c0b1fa535921b7b33a16f55bdc8b76d6125e72
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704095"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Nasıl yapılır: INotifyPropertyChanged arabirimini uygulama
Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygulayın. Arabirim uygulandığında, ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerinin iletişim kurar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: PropertyNameChanged desenini uygulama](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri Yükselt](./controls/raise-change-notifications--bindingsource.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
