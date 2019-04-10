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
ms.openlocfilehash: 160d1b5f0604cff96549c9d94dc5d8ddc7e39f09
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217165"
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a>Nasıl yapılır: Windows Hizmetini Devam Ettirme (Visual Basic)
Bu örnekte <xref:System.ServiceProcess.ServiceController> IIS Yönetici Hizmeti yerel bilgisayarda devam etmek için bileşen.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **Windows işletim sistemi > Windows Hizmetleri**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir proje başvurusu System.serviceprocess.dll'ye.  
  
-   Üye erişimi <xref:System.ServiceProcess> ad alanı. Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Özelliği <xref:System.ServiceProcess.ServiceController> sınıfı varsayılan olarak yerel bilgisayardır. Başka bir bilgisayarda Windows Hizmetleri başvurmak için değişiklik <xref:System.ServiceProcess.ServiceController.MachineName%2A> özelliğini bilgisayarın adı.  
  
 Çağıramazsınız <xref:System.ServiceProcess.ServiceController.Continue%2A> yöntemi bir hizmete ait hizmet denetleyicisi durumu: kadar <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.  
  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Hizmeti devam ettirilemiyor. (<xref:System.InvalidOperationException>)  
  
-   Bir sistem API'si erişirken bir hata oluştu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bilgisayardaki hizmetlerin denetimi kullanılarak kısıtlanabilir <xref:System.ServiceProcess.ServiceControllerPermissionAccess> izinleri ayarlamak için numaralandırma <xref:System.ServiceProcess.ServiceControllerPermission> sınıfı.  
  
 Kullanarak hizmet bilgilere erişimi kısıtlanabilir <xref:System.Security.Permissions.PermissionState> izinleri ayarlamak için numaralandırma <xref:System.Security.Permissions.SecurityPermission> sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- [Nasıl yapılır: Windows Hizmetini Duraklatma (Visual Basic)](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
