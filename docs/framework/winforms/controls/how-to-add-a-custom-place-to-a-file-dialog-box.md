---
title: 'Nasıl yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916344"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Nasıl yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme
Varsayılan aç ve Kaydet iletişim kutuları [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] , **sık kullanılan bağlantılar**başlıklı iletişim kutusunun sol tarafında bir alana sahiptir. Bu alana özel yer denir. <xref:System.Windows.Forms.OpenFileDialog> Ve sınıfları<xref:System.Windows.Forms.SaveFileDialog>koleksiyonaklasörler <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> eklemenize olanak tanır.  
  
> [!NOTE]
> Özel bir yeri <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>içinde görünmesi için, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği olarak `true` ayarlanmalıdır (varsayılan).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Bir dosya iletişim kutusuna özel bir yer eklemek için  
  
- İletişim kutusu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonuna bir yol, bilinen bir klasör GUID 'i <xref:System.Windows.Forms.FileDialogCustomPlace> veya nesne ekleyin.  
  
     Aşağıdaki kod örneği, bir yolun nasıl ekleneceğini göstermektedir:  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [Dosya İletişim Kutusu Özel Yerleri İçin Bilinen Klasör GUID'leri](known-folder-guids-for-file-dialog-custom-places.md)
