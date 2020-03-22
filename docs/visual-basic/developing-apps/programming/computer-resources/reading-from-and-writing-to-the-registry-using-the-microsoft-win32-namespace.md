---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345492"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)

Kayıt `My.Computer.Registry` defterine karşı programlama yaparken temel gereksinimlerinizi karşılamanız <xref:Microsoft.Win32.Registry> gerekse <xref:Microsoft.Win32> de, .NET Framework'ün ad alanında ve <xref:Microsoft.Win32.RegistryKey> sınıfları da kullanabilirsiniz.  
  
## <a name="keys-in-the-registry-class"></a>Kayıt Defteri Sınıfındaki Anahtarlar  

 Sınıf, <xref:Microsoft.Win32.Registry> alt anahtarlara ve değerlerine erişmek için kullanılabilecek temel kayıt defteri anahtarlarını sağlar. Temel anahtarların kendileri salt okunur. Aşağıdaki tablo listeler ve <xref:Microsoft.Win32.Registry> sınıf tarafından maruz yedi tuşları açıklar.  
  
|**Anahtar**|**Açıklama**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Belge türlerini ve bu türlerle ilişkili özellikleri tanımlar.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Kullanıcıya özel olmayan donanım yapılandırma bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Çevresel değişkenler gibi geçerli kullanıcı tercihleri hakkında bilgi içerir.|  
|<xref:Microsoft.Win32.Registry.DynData>|Sanal Aygıt Sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Yerel bilgisayarın yapılandırma verilerini tutan beş alt anahtar (Donanım, SAM, Güvenlik, Yazılım ve Sistem) içerir.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Yazılım bileşenleri için performans bilgileri içerir.|  
|<xref:Microsoft.Win32.Registry.Users>|Varsayılan kullanıcı tercihleri hakkında bilgi içerir.|  
  
> [!IMPORTANT]
> Yerel bilgisayara ()<xref:Microsoft.Win32.Registry.CurrentUser>veri yazmak, () mevcut kullanıcıya yazmak daha güvenlidir.<xref:Microsoft.Win32.Registry.LocalMachine> Genellikle "çömelme" olarak adlandırılan bir koşul, oluşturduğunuz anahtar daha önce başka bir kötü amaçlı işlem tarafından oluşturulduğunda oluşur. Bunun oluşmasını önlemek için, anahtar <xref:Microsoft.Win32.RegistryKey.GetValue%2A>zaten yoksa `Nothing` döndüren bir yöntem kullanın.  
  
## <a name="reading-a-value-from-the-registry"></a>Kayıt Defterinden Değer Okuma  

 Aşağıdaki kod, HKEY_CURRENT_USER bir dizenasıl okunduğunu gösterir.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Aşağıdaki kod okur, artışlar ve sonra HKEY_CURRENT_USER için bir dize yazar.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Deneyin... Yakalamak... Son İfade](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Güvenlik ve Kayıt Defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
