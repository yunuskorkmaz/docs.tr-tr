---
title: 'Nasıl yapılır: Dosya iletişim kutusuna özel yer ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 797b98cb408c7f9fc1d55b774f7ceccef009bb22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674654"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Nasıl yapılır: Dosya iletişim kutusuna özel yer ekleme
Varsayılan açın ve iletişim kutuları tasarruf [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] başlıklı iletişim kutusunun sol tarafında bir alana sahip **sık kullanılan bağlantılar**. Bu alanı özel yerler çağrılır. <xref:System.Windows.Forms.OpenFileDialog> Ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları klasörlere eklemenize izin <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonu.  
  
> [!NOTE]
>  Görünmesi özel bir alan için sırayla <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği ayarlanmalıdır `true` (varsayılan).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Dosya iletişim kutusuna özel yer ekleme  
  
-   Bilinen klasör GUID, bir yol eklemek veya bir <xref:System.Windows.Forms.FileDialogCustomPlace> nesnesini <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> iletişim kutusunun koleksiyonu.  
  
     Aşağıdaki kod örneği, bir yol eklemek gösterilmektedir:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [Dosya İletişim Kutusu Özel Yerleri İçin Bilinen Klasör GUID'leri](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
