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
ms.openlocfilehash: 79836dd260cb13912ccba43cfb4a0a3e0ad195fd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087696"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="02869-102">Nasıl yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme</span><span class="sxs-lookup"><span data-stu-id="02869-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="02869-103">Varsayılan açın ve iletişim kutuları tasarruf [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] başlıklı iletişim kutusunun sol tarafında bir alana sahip **sık kullanılan bağlantılar**.</span><span class="sxs-lookup"><span data-stu-id="02869-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="02869-104">Bu alanı özel yerler çağrılır.</span><span class="sxs-lookup"><span data-stu-id="02869-104">This area is called custom places.</span></span> <span data-ttu-id="02869-105"><xref:System.Windows.Forms.OpenFileDialog> Ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları klasörlere eklemenize izin <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="02869-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02869-106">Görünmesi özel bir alan için sırayla <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği ayarlanmalıdır `true` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="02869-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="02869-107">Dosya iletişim kutusuna özel yer ekleme</span><span class="sxs-lookup"><span data-stu-id="02869-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="02869-108">Bilinen klasör GUID, bir yol eklemek veya bir <xref:System.Windows.Forms.FileDialogCustomPlace> nesnesini <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> iletişim kutusunun koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="02869-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="02869-109">Aşağıdaki kod örneği, bir yol eklemek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="02869-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02869-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02869-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="02869-111">Dosya İletişim Kutusu Özel Yerleri İçin Bilinen Klasör GUID'leri</span><span class="sxs-lookup"><span data-stu-id="02869-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
