---
title: 'Nasıl yapılır: Windows Forms’da Bir Dosyayla İlişkili Simgeyi Çıkarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: c3173a3fa756a3294154217f5cf0a13dbc8721f3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645408"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a><span data-ttu-id="4f2cb-102">Nasıl yapılır: Windows Forms’da Bir Dosyayla İlişkili Simgeyi Çıkarma</span><span class="sxs-lookup"><span data-stu-id="4f2cb-102">How to: Extract the Icon Associated with a File in Windows Forms</span></span>
<span data-ttu-id="4f2cb-103">Çok sayıda dosya sağlayan bir görsel bir temsili ilişkili dosya türü simgeleri katıştırılmış sahip.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-103">Many files have embedded icons that provide a visual representation of the associated file type.</span></span> <span data-ttu-id="4f2cb-104">Örneğin, Microsoft Word belgeleri, bunları Word belgeleri olarak tanımlayan bir simge içerir.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-104">For example, Microsoft Word documents contain an icon that identifies them as Word documents.</span></span> <span data-ttu-id="4f2cb-105">Liste denetimi ya da tablo denetim dosyaları görüntülerken, her dosya adının yanındaki dosya türünü temsil eden bir simge görüntülemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-105">When displaying files in a list control or table control, you may want to display the icon representing the file type next to each file name.</span></span> <span data-ttu-id="4f2cb-106">Kolayca kullanarak bunu yapabilirsiniz <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-106">You can do this easily by using the <xref:System.Drawing.Icon.ExtractAssociatedIcon%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f2cb-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f2cb-107">Example</span></span>  
 <span data-ttu-id="4f2cb-108">Aşağıdaki kod örneği bir dosyayla ilişkili simgeyi çıkarma ve görüntü dosya adı ve ilgili simgeye yapmayı gösteren bir <xref:System.Windows.Forms.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-108">The following code example demonstrates how to extract the icon associated with a file and display the file name and its associated icon in a <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f2cb-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4f2cb-109">Compiling the Code</span></span>  
 <span data-ttu-id="4f2cb-110">Örneği derlemek için:</span><span class="sxs-lookup"><span data-stu-id="4f2cb-110">To compile the example:</span></span>  
  
- <span data-ttu-id="4f2cb-111">Yukarıdaki kod, bir Windows Form ve çağrı yapıştırın `ExtractAssociatedIconExample` formun oluşturucudan yöntemi veya <xref:System.Windows.Forms.Form.Load> olay işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-111">Paste the preceding code into a Windows Form, and call the `ExtractAssociatedIconExample` method from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     <span data-ttu-id="4f2cb-112">Formunuza alındığından emin olmak ihtiyacınız olacak <xref:System.IO> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-112">You will need to make sure that your form imports the <xref:System.IO> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2cb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f2cb-113">See also</span></span>

- [<span data-ttu-id="4f2cb-114">Görüntüler, Bit Eşlemler ve Meta Dosyaları</span><span class="sxs-lookup"><span data-stu-id="4f2cb-114">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="4f2cb-115">ListView Denetimi</span><span class="sxs-lookup"><span data-stu-id="4f2cb-115">ListView Control</span></span>](../controls/listview-control-windows-forms.md)
