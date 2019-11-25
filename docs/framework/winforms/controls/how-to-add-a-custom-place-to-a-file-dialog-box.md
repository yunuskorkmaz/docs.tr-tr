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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="9614d-102">Nasıl Yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme</span><span class="sxs-lookup"><span data-stu-id="9614d-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="9614d-103">Windows Vista 'daki varsayılan aç ve Kaydet iletişim kutuları, **sık kullanılan bağlantılar**başlıklı iletişim kutusunun sol tarafındaki bir alana sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9614d-103">The default open and save dialog boxes on Windows Vista have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="9614d-104">Bu alana özel yer denir.</span><span class="sxs-lookup"><span data-stu-id="9614d-104">This area is called custom places.</span></span> <span data-ttu-id="9614d-105"><xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonuna klasörler eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9614d-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9614d-106"><xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>özel bir yer görünmesi için <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği `true` olarak ayarlanmalıdır (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="9614d-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="9614d-107">Bir dosya iletişim kutusuna özel bir yer eklemek için</span><span class="sxs-lookup"><span data-stu-id="9614d-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="9614d-108">İletişim kutusunun <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonuna bir yol, bilinen bir klasör GUID 'i veya bir <xref:System.Windows.Forms.FileDialogCustomPlace> nesnesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9614d-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="9614d-109">Aşağıdaki kod örneği, bir yolun nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9614d-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9614d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9614d-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9614d-111">Dosya İletişim Kutusu Özel Yerleri İçin Bilinen Klasör GUID'leri</span><span class="sxs-lookup"><span data-stu-id="9614d-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
