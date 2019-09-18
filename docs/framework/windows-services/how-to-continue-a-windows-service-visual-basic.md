---
title: 'Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)'
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
ms.openlocfilehash: a10e05b0460608a9e67ee4527adf80be3d47438e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053632"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)
Bu örnek, yerel <xref:System.ServiceProcess.ServiceController> bilgisayarda IIS Yönetim hizmetine devam etmek için bileşenini kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System. ServiceProcess. dll dosyasına bir proje başvurusu.  
  
- <xref:System.ServiceProcess> Ad alanının üyelerine erişin. Kodunuzda üye `Imports` adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController> Sınıfının özelliği, varsayılan olarak yerel bilgisayardır. <xref:System.ServiceProcess.ServiceController.MachineName%2A> Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.  
  
 Hizmet denetleyicisi <xref:System.ServiceProcess.ServiceController.Continue%2A> <xref:System.ServiceProcess.ServiceControllerStatus.Paused>durumu olana kadar bir hizmette yöntemi çağrılamaz.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Hizmet devam ettirilemiyor. (<xref:System.InvalidOperationException>)  
  
- Sistem API 'sine erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> <xref:System.ServiceProcess.ServiceControllerPermission> sınıftaki izinleri ayarlamak için sabit listesi kullanılarak kısıtlanabilir.  
  
 Sınıfında<xref:System.Security.Permissions.SecurityPermission> izinleri ayarlamak için <xref:System.Security.Permissions.PermissionState> numaralandırma kullanılarak hizmet bilgilerine erişim kısıtlanabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [Nasıl yapılır: Bir Windows hizmetini duraklatma (Visual Basic)](how-to-pause-a-windows-service-visual-basic.md)
