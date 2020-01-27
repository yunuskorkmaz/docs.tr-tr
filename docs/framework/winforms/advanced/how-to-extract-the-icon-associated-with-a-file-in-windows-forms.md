---
title: 'Nasıl yapılır: bir dosyayla Ilişkili simgeyi ayıklama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 28769144b0e1c631a31c3c541747a6215f861d0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742547"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="6dd23-102">Nasıl yapılır: Windows Formlarında Bir Dosyayla İlişkili Simgeyi Çıkarma</span><span class="sxs-lookup"><span data-stu-id="6dd23-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="6dd23-103">Birçok dosya, ilişkili dosya türünün görsel gösterimini sağlayan katıştırılmış simgelere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6dd23-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="6dd23-104">Örneğin, Microsoft Word belgeleri bunları Word belgeleri olarak tanımlayan bir simge içerir.</span><span class="sxs-lookup"><span data-stu-id="6dd23-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="6dd23-105">Bir liste denetimindeki veya tablo denetimindeki dosyaları görüntülerken, her dosya adının yanında dosya türünü temsil eden simgeyi görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dd23-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="6dd23-106"><xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> yöntemini kullanarak bunu kolayca yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dd23-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dd23-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6dd23-107">Example</span></span>  
 <span data-ttu-id="6dd23-108">Aşağıdaki kod örneği, bir dosyayla ilişkili simgenin nasıl ayıklanacağını ve dosya adını ve ilişkili simgesini bir <xref:System.Windows.Forms.ListView> denetiminde görüntülemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dd23-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6dd23-109">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="6dd23-109">Compiling the Code</span></span>  
 <span data-ttu-id="6dd23-110">Örneği derlemek için:</span><span class="sxs-lookup"><span data-stu-id="6dd23-110">To compile the example:</span></span>  
  
- <span data-ttu-id="6dd23-111">Önceki kodu bir Windows formuna yapıştırın ve formun Oluşturucu veya <xref:System.Windows.Forms.Form.Load> olay işleme yönteminden `ExtractAssociatedIconExample` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="6dd23-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="6dd23-112">Formunuzun <xref:System.IO> ad alanını içeri aktardığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6dd23-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd23-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dd23-113">See also</span></span>

- [<span data-ttu-id="6dd23-114">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="6dd23-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="6dd23-115">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="6dd23-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
