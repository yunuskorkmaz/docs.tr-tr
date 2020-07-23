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
author: ghogen
ms.openlocfilehash: 2a04e330ea7dc37552053b2a7915909c011727f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925793"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)
Bu örnek, <xref:System.ServiceProcess.ServiceController> Yerel bılgısayarda IIS Yönetim hizmetine devam etmek için bileşenini kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, Windows **Işletim sistemi > Windows Hizmetleri**' nde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System.serviceprocess.dll bir proje başvurusu.  
  
- <xref:System.ServiceProcess>Ad alanının üyelerine erişin. `Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A>Sınıfının özelliği, <xref:System.ServiceProcess.ServiceController> Varsayılan olarak yerel bilgisayardır. Başka bir bilgisayardaki Windows hizmetlerine başvurmak için, <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliği bu bilgisayarın adıyla değiştirin.  
  
 <xref:System.ServiceProcess.ServiceController.Continue%2A>Hizmet denetleyicisi durumu olana kadar bir hizmette yöntemi çağrılamaz <xref:System.ServiceProcess.ServiceControllerStatus.Paused> .  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Hizmet devam ettirilemiyor. (<xref:System.InvalidOperationException>)  
  
- Sistem API 'sine erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi, <xref:System.ServiceProcess.ServiceControllerPermissionAccess> sınıftaki izinleri ayarlamak için sabit listesi kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermission> .  
  
 <xref:System.Security.Permissions.PermissionState>Sınıfında izinleri ayarlamak için numaralandırma kullanılarak hizmet bilgilerine erişim kısıtlanabilir <xref:System.Security.Permissions.SecurityPermission> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)](how-to-pause-a-windows-service-visual-basic.md)
