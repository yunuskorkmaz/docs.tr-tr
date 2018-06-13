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
ms.openlocfilehash: 42940654a0754ac3616ca7983af07d20607f480f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522275"
---
# <a name="how-to-print-a-windows-form"></a><span data-ttu-id="538da-102">Nasıl yapılır: Bir Windows Formunu Yazdırma</span><span class="sxs-lookup"><span data-stu-id="538da-102">How to: Print a Windows Form</span></span>
<span data-ttu-id="538da-103">Geliştirme sürecinin bir parçası olarak, genellikle Windows formu bir kopyasını yazdırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="538da-103">As part of the development process, you typically will want to print a copy of your Windows Form.</span></span> <span data-ttu-id="538da-104">Aşağıdaki kod örneğinde geçerli formun bir kopyasını kullanarak yazdırma gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="538da-104">The following code example shows how to print a copy of the current form by using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="538da-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="538da-105">Example</span></span>  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="538da-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="538da-106">Compiling the Code</span></span>  
 <span data-ttu-id="538da-107">Bu içeren bir tam bir kod örneğidir bir `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="538da-107">This is a complete code example that contains a `Main` method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="538da-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="538da-108">Robust Programming</span></span>  
 <span data-ttu-id="538da-109">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="538da-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="538da-110">Yazıcı erişim iznine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="538da-110">You do not have permission to access the printer.</span></span>  
  
-   <span data-ttu-id="538da-111">Yazıcı yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="538da-111">There is no printer installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="538da-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="538da-112">.NET Framework Security</span></span>  
 <span data-ttu-id="538da-113">Bu kod örneği çalıştırmak için bilgisayarınızda kullandığınız yazıcıya erişim izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="538da-113">In order to run this code example, you must have permission to access the printer you use with your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="538da-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="538da-114">See Also</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="538da-115">Nasıl yapılır: GDI+ ile Görüntü İşleme</span><span class="sxs-lookup"><span data-stu-id="538da-115">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [<span data-ttu-id="538da-116">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="538da-116">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
