---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme ile sanal modu uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: 0aeba7c39bb19de0300e166936e3f8b8f70f83b0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702808"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="4b999-102">Nasıl yapılır: Windows Forms DataGridView denetiminde tam zamanında veri yükleme ile sanal modu uygulama</span><span class="sxs-lookup"><span data-stu-id="4b999-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4b999-103">Aşağıdaki kod örneği, sanal modda kullanmayı gösterilmektedir <xref:System.Windows.Forms.DataGridView> denetimi yalnızca gerekli olduğunda bir sunucudan veri yükleyen bir veri önbelleği ile.</span><span class="sxs-lookup"><span data-stu-id="4b999-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="4b999-104">Bu örnekte, ayrıntılı olarak açıklanan [ile tam zamanında veri yükleme Windows Forms DataGridView denetiminde sanal modu uygulama](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="4b999-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b999-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b999-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b999-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4b999-106">Compiling the Code</span></span>  
 <span data-ttu-id="4b999-107">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4b999-107">This example requires:</span></span>  
  
-   <span data-ttu-id="4b999-108">Sistem, System.Data System.Xml ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="4b999-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="4b999-109">Yüklü SQL Server Northwind örnek veritabanı ile bir sunucu erişim.</span><span class="sxs-lookup"><span data-stu-id="4b999-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
 <span data-ttu-id="4b999-110">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4b999-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="4b999-111">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4b999-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4b999-112">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4b999-112">.NET Framework Security</span></span>  
 <span data-ttu-id="4b999-113">Depolama bağlantı dizesi içinde bir parola gibi hassas bilgileri, uygulamanızın güvenliğini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4b999-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="4b999-114">Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="4b999-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="4b999-115">Daha fazla bilgi için [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="4b999-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b999-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b999-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="4b999-117">Windows Forms DataGridView Denetiminde Zamanında Veri Yükleme ile Sanal Modu Uygulama</span><span class="sxs-lookup"><span data-stu-id="4b999-117">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="4b999-118">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="4b999-118">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="4b999-119">Windows Forms DataGridView Denetiminde Sanal Mod</span><span class="sxs-lookup"><span data-stu-id="4b999-119">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
