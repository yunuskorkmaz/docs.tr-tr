---
title: 'Nasıl Yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 7172e484451cf932413920910ec9124b3388bd76
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976984"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>Nasıl Yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme
Windows Vista 'daki varsayılan aç ve Kaydet iletişim kutuları, **sık kullanılan bağlantılar**başlıklı iletişim kutusunun sol tarafındaki bir alana sahiptir. Bu alana özel yer denir. <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonuna klasörler eklemenize olanak tanır.  
  
> [!NOTE]
> <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>özel bir yer görünmesi için <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği `true` olarak ayarlanmalıdır (varsayılan).  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>Bir dosya iletişim kutusuna özel bir yer eklemek için  
  
- İletişim kutusunun <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonuna bir yol, bilinen bir klasör GUID 'i veya bir <xref:System.Windows.Forms.FileDialogCustomPlace> nesnesi ekleyin.  
  
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
