---
title: 'Nasıl yapılır: Bir Windows Formunu Yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: 85fb12028687578b76e0f16061deb9b9a4de70e3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121972"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="8d882-102">Nasıl yapılır: Bir Windows Formunu Yazdırma</span><span class="sxs-lookup"><span data-stu-id="8d882-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="8d882-103">Geliştirme sürecinin bir parçası olarak, genellikle Windows formunuza bir kopyasını yazdırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="8d882-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="8d882-104">Aşağıdaki kod örneği kullanarak geçerli forma bir kopyasını yazdırmak gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8d882-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d882-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d882-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d882-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8d882-106">Compiling the Code</span></span>  
 <span data-ttu-id="8d882-107">İçeren tam bir kod örneğini budur bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8d882-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8d882-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="8d882-108">Robust Programming</span></span>  
 <span data-ttu-id="8d882-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8d882-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8d882-110">Yazıcı erişmek için izniniz yok.</span><span class="sxs-lookup"><span data-stu-id="8d882-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="8d882-111">Yüklü yazıcı yok yoktur.</span><span class="sxs-lookup"><span data-stu-id="8d882-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8d882-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8d882-112">.NET Framework Security</span></span>  
 <span data-ttu-id="8d882-113">Bu kod örneği çalıştırmak için bilgisayarınızda kullandığınız yazıcıya erişim izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d882-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d882-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d882-114">See also</span></span>

- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="8d882-115">Nasıl yapılır: GDI + ile görüntü işleme</span><span class="sxs-lookup"><span data-stu-id="8d882-115">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
- [<span data-ttu-id="8d882-116">Nasıl yapılır: Windows Forms'ta grafik yazdırma</span><span class="sxs-lookup"><span data-stu-id="8d882-116">How to: Print Graphics in Windows Forms</span></span>](how-to-print-graphics-in-windows-forms.md)
