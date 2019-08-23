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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="dfc34-102">Nasıl yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme</span><span class="sxs-lookup"><span data-stu-id="dfc34-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="dfc34-103">Varsayılan aç ve Kaydet iletişim kutuları [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] , **sık kullanılan bağlantılar**başlıklı iletişim kutusunun sol tarafında bir alana sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dfc34-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="dfc34-104">Bu alana özel yer denir.</span><span class="sxs-lookup"><span data-stu-id="dfc34-104">This area is called custom places.</span></span> <span data-ttu-id="dfc34-105"><xref:System.Windows.Forms.OpenFileDialog> Ve sınıfları<xref:System.Windows.Forms.SaveFileDialog>koleksiyonaklasörler <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dfc34-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfc34-106">Özel bir yeri <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>içinde görünmesi için, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği olarak `true` ayarlanmalıdır (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="dfc34-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="dfc34-107">Bir dosya iletişim kutusuna özel bir yer eklemek için</span><span class="sxs-lookup"><span data-stu-id="dfc34-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="dfc34-108">İletişim kutusu <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonuna bir yol, bilinen bir klasör GUID 'i <xref:System.Windows.Forms.FileDialogCustomPlace> veya nesne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dfc34-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="dfc34-109">Aşağıdaki kod örneği, bir yolun nasıl ekleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="dfc34-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dfc34-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc34-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="dfc34-111">Dosya İletişim Kutusu Özel Yerleri İçin Bilinen Klasör GUID'leri</span><span class="sxs-lookup"><span data-stu-id="dfc34-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
