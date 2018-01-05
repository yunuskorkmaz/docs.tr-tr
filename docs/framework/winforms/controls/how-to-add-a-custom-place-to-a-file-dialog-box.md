---
title: "Nasıl Yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme"
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
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1a10a58552dd416084da39838a9e36f15e85074
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="5d3d2-102">Nasıl Yapılır: Dosya İletişim Kutusuna Özel Yer Ekleme</span><span class="sxs-lookup"><span data-stu-id="5d3d2-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="5d3d2-103">Varsayılan açın ve iletişim kutuları kaydetmek [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] başlıklı iletişim kutusunun sol tarafında bir alana sahip **sık kullanılan bağlantılar**.</span><span class="sxs-lookup"><span data-stu-id="5d3d2-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="5d3d2-104">Bu alan özel yerler adı verilir.</span><span class="sxs-lookup"><span data-stu-id="5d3d2-104">This area is called custom places.</span></span> <span data-ttu-id="5d3d2-105"><xref:System.Windows.Forms.OpenFileDialog> Ve <xref:System.Windows.Forms.SaveFileDialog> sınıfları klasörlere eklemenize izin <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5d3d2-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d3d2-106">Görünmesi özel bir yere sırayla <xref:System.Windows.Forms.OpenFileDialog> veya <xref:System.Windows.Forms.SaveFileDialog>, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> özelliği ayarlanmalıdır `true` (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="5d3d2-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="5d3d2-107">Dosya iletişim kutusuna özel yer eklemek için</span><span class="sxs-lookup"><span data-stu-id="5d3d2-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="5d3d2-108">Bir bilinen klasör GUID bir yolu ekleyin veya bir <xref:System.Windows.Forms.FileDialogCustomPlace> nesnesine <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> iletişim kutusunun koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5d3d2-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="5d3d2-109">Aşağıdaki kod örneği, bir yol eklemek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5d3d2-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5d3d2-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d3d2-110">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5d3d2-111">Dosya İletişim Kutusu Özel Yerleri İçin Bilinen Klasör GUID'leri</span><span class="sxs-lookup"><span data-stu-id="5d3d2-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
