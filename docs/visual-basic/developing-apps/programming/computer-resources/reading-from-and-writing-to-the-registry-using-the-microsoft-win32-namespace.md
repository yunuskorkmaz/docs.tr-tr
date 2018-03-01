---
title: "Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 462cc5c3854035cfc04c7c5df6905c2cfbd486ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)
Ancak `My.Computer.Registry` temel gereksinimlerinizi kayıt defteri karşı programlama zaman kapsaması gereken, aynı zamanda <xref:Microsoft.Win32.Registry> ve <xref:Microsoft.Win32.RegistryKey> sınıfları <xref:Microsoft.Win32> ad alanı [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Kayıt defteri sınıfı anahtarları  
 <xref:Microsoft.Win32.Registry> Sınıfı alt anahtarları ve değerleri erişmek için kullanılan temel kayıt defteri anahtarlarını sağlar. Temel anahtarları salt okunurdur. Aşağıdaki tabloda listelenmekte ve tarafından sunulan yedi anahtarları açıklanmaktadır <xref:Microsoft.Win32.Registry> sınıfı.  
  
|**Anahtarı**|**Açıklama**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Belgeler ve bu türleriyle ilişkili özellikleri türlerini tanımlar.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Geçerli kullanıcı tercihleri gibi ortam değişkenleri hakkında bilgi içerir.|  
|<xref:Microsoft.Win32.Registry.DynData>|Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verilerini içerir.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Yerel bilgisayar için yapılandırma verilerini tutan beş alt anahtarları (donanım, SAM, güvenlik, yazılım ve sistem) içerir.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Yazılım bileşenleri için performans bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.Users>|Varsayılan kullanıcı tercihleri hakkında bilgi içerir.|  
  
> [!IMPORTANT]
>  Geçerli kullanıcının veri yazmak için daha güvenlidir (<xref:Microsoft.Win32.Registry.CurrentUser>) daha yerel bilgisayarda (<xref:Microsoft.Win32.Registry.LocalMachine>). Anahtar, oluştururken "ele geçirme" gerçekleştiği sırada, genellikle başvurulan bir koşul, daha önce başka bir, büyük olasılıkla kötü amaçlı işlem tarafından oluşturuldu. Bu oluşmasını önlemek için bir yöntem gibi kullanın <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, döndüren `Nothing` anahtarı zaten mevcut değilse.  
  
## <a name="reading-a-value-from-the-registry"></a>Kayıt defteri anahtarından değer okuma  
 Aşağıdaki kod, bir dize HKEY_CURRENT_USER okuma gösterilmektedir.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 Aşağıdaki kod, artışlarla okur ve ardından bir dize HKEY_CURRENT_USER yazar.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [Try... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Okuma ve kayıt defterine yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Güvenlik ve kayıt defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
