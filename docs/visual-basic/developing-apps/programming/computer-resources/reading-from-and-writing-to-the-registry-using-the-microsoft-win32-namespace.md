---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: d55bd991587016aee48a522b69fdbdb5d4041512
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530833"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)
Ancak `My.Computer.Registry` gereksinimlerinizi temel kayıt defteri karşı programlama yaparken kapsamalıdır, ayrıca <xref:Microsoft.Win32.Registry> ve <xref:Microsoft.Win32.RegistryKey> sınıfları <xref:Microsoft.Win32> ad [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Kayıt defteri sınıfı anahtarları  
 <xref:Microsoft.Win32.Registry> Sınıfı alt anahtarları ve değerlerini erişmek için kullanılan temel kayıt defteri anahtarlarını sağlar. Temel anahtarları salt okunurdur. Aşağıdaki tabloda listelenmiş ve açıklar tarafından kullanıma sunulan yedi anahtarları <xref:Microsoft.Win32.Registry> sınıfı.  
  
|**Key**|**Açıklama**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Belgeler ve bu türleriyle ilişkili özellikleri türlerini tanımlar.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Geçerli kullanıcı tercihleri gibi ortam değişkenleri hakkında bilgi içerir.|  
|<xref:Microsoft.Win32.Registry.DynData>|Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Yerel bilgisayar için yapılandırma verilerini tutun beş alt (donanım, SAM, güvenlik, yazılım ve sistem) içerir.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Yazılım bileşenlerinin performans bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.Users>|Varsayılan kullanıcı tercihlerini hakkında bilgi içerir.|  
  
> [!IMPORTANT]
>  Geçerli kullanıcıya veri yazmak için daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) değerinden yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>). Anahtar, oluştururken "ele geçirme" gerçekleştiği sırada genellikle adlandırılır bir koşul, daha önce başka bir, büyük olasılıkla kötü amaçlı işlemi tarafından oluşturuldu. Bunun gerçekleşmesini önlemek için bir yöntem gibi kullanın <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, döndüren `Nothing` anahtarı zaten mevcut değilse.  
  
## <a name="reading-a-value-from-the-registry"></a>Bir değeri Kayıt Defteri'nden okuma  
 Aşağıdaki kod, bir dize HKEY_CURRENT_USER okumak gösterilmektedir.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 Aşağıdaki kod, artışlarla okur ve sonra bir dize HKEY_CURRENT_USER üzerine yazar.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Güvenlik ve Kayıt Defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
