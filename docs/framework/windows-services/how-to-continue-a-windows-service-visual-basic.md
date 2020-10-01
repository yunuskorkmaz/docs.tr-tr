---
title: 'Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)'
description: Visual Basic olan yerel bir bilgisayarda bir Windows hizmetine (IIS Yönetim hizmeti gibi) devam etmek için ServiceController bileşenini nasıl kullanacağınızı okuyun.
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
ms.openlocfilehash: 9e672a19cec814694eddb35672c5c669efd40eb2
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608614"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="c0979-103">Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0979-103">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="c0979-104">Bu örnek, <xref:System.ServiceProcess.ServiceController> Yerel bılgısayarda IIS Yönetim hizmetine devam etmek için bileşenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0979-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0979-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0979-105">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="c0979-106">Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0979-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="c0979-107">Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur.</span><span class="sxs-lookup"><span data-stu-id="c0979-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="c0979-108">Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="c0979-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c0979-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="c0979-109">Compiling the Code</span></span>  
 <span data-ttu-id="c0979-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c0979-110">This example requires:</span></span>  
  
- <span data-ttu-id="c0979-111">System.serviceprocess.dll bir proje başvurusu.</span><span class="sxs-lookup"><span data-stu-id="c0979-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="c0979-112"><xref:System.ServiceProcess>Ad alanının üyelerine erişin.</span><span class="sxs-lookup"><span data-stu-id="c0979-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="c0979-113">`Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c0979-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c0979-114">Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c0979-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c0979-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c0979-115">Robust Programming</span></span>  
 <span data-ttu-id="c0979-116"><xref:System.ServiceProcess.ServiceController.MachineName%2A>Sınıfının özelliği, <xref:System.ServiceProcess.ServiceController> Varsayılan olarak yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="c0979-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="c0979-117">Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c0979-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="c0979-118"><xref:System.ServiceProcess.ServiceController.Continue%2A>Hizmet denetleyicisi durumu olana kadar bir hizmette yöntemi çağrılamaz <xref:System.ServiceProcess.ServiceControllerStatus.Paused> .</span><span class="sxs-lookup"><span data-stu-id="c0979-118">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="c0979-119">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c0979-119">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c0979-120">Hizmet devam ettirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="c0979-120">The service cannot be resumed.</span></span> <span data-ttu-id="c0979-121">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="c0979-121">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="c0979-122">Sistem API 'sine erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c0979-122">An error occurred when accessing a system API.</span></span> <span data-ttu-id="c0979-123">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="c0979-123">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c0979-124">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c0979-124">.NET Framework Security</span></span>  
 <span data-ttu-id="c0979-125">Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> sınıftaki izinleri ayarlamak için sabit listesi kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermission> .</span><span class="sxs-lookup"><span data-stu-id="c0979-125">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="c0979-126"><xref:System.Security.Permissions.PermissionState>Sınıfında izinleri ayarlamak için numaralandırma kullanılarak hizmet bilgilerine erişim kısıtlanabilir <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="c0979-126">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0979-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0979-127">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="c0979-128">Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0979-128">How to: Pause a Windows Service (Visual Basic)</span></span>](how-to-pause-a-windows-service-visual-basic.md)
