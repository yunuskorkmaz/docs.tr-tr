---
title: 'Nasıl yapılır: Bir Windows hizmeti (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
author: ghogen
ms.openlocfilehash: 86c2414fd6ad9c32a37339c553ec80c98426f78a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612716"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="bb1fb-102">Nasıl yapılır: Bir Windows hizmeti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb1fb-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="bb1fb-103">Bu örnekte <xref:System.ServiceProcess.ServiceController> IIS Yönetici Hizmeti yerel bilgisayarda devam etmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb1fb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb1fb-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="bb1fb-105">Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="bb1fb-106">Kod parçacığı Seçici'de bulunur **Windows işletim sistemi > Windows Hizmetleri**.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="bb1fb-107">Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="bb1fb-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb1fb-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bb1fb-108">Compiling the Code</span></span>  
 <span data-ttu-id="bb1fb-109">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="bb1fb-109">This example requires:</span></span>  
  
-   <span data-ttu-id="bb1fb-110">Bir proje başvurusu System.serviceprocess.dll'ye.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="bb1fb-111">Üye erişimi <xref:System.ServiceProcess> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="bb1fb-112">Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="bb1fb-113">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="bb1fb-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bb1fb-114">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="bb1fb-114">Robust Programming</span></span>  
 <span data-ttu-id="bb1fb-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A> Özelliği <xref:System.ServiceProcess.ServiceController> sınıfı varsayılan olarak yerel bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="bb1fb-116">Başka bir bilgisayarda Windows Hizmetleri başvurmak için değişiklik <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliğini bilgisayarın adı.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="bb1fb-117">Çağıramazsınız <xref:System.ServiceProcess.ServiceController.Continue%2A> yöntemi bir hizmete ait hizmet denetleyicisi durumu: kadar <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="bb1fb-118">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="bb1fb-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="bb1fb-119">Hizmeti devam ettirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-119">The service cannot be resumed.</span></span> <span data-ttu-id="bb1fb-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="bb1fb-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="bb1fb-121">Bir sistem API'si erişirken bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="bb1fb-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="bb1fb-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bb1fb-123">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="bb1fb-123">.NET Framework Security</span></span>  
 <span data-ttu-id="bb1fb-124">Bilgisayardaki hizmetlerin denetimi kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermissionAccess> izinleri ayarlamak için numaralandırma <xref:System.ServiceProcess.ServiceControllerPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="bb1fb-125">Kullanarak hizmet bilgilere erişimi kısıtlanabilir <xref:System.Security.Permissions.PermissionState> izinleri ayarlamak için numaralandırma <xref:System.Security.Permissions.SecurityPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1fb-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb1fb-126">See also</span></span>
- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [<span data-ttu-id="bb1fb-127">Nasıl yapılır: (Visual Basic) bir Windows hizmetini duraklatma</span><span class="sxs-lookup"><span data-stu-id="bb1fb-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
