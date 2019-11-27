---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345492"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)

Kayıt defterinde programlama yaparken `My.Computer.Registry` temel ihtiyaçlarınızı kapsasa da, .NET Framework <xref:Microsoft.Win32> ad alanındaki <xref:Microsoft.Win32.Registry> ve <xref:Microsoft.Win32.RegistryKey> sınıflarını da kullanabilirsiniz.  
  
## <a name="keys-in-the-registry-class"></a>Kayıt defteri sınıfındaki anahtarlar  

 <xref:Microsoft.Win32.Registry> sınıfı, alt anahtarlara ve değerlerine erişmek için kullanılabilen temel kayıt defteri anahtarlarını sağlar. Temel anahtarlar salt okunurdur. Aşağıdaki tabloda <xref:Microsoft.Win32.Registry> sınıfı tarafından kullanıma sunulan yedi anahtar listelenmektedir ve açıklanmaktadır.  
  
|**Key**|**Açıklama**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Belge türlerini ve bu türlerle ilişkili özellikleri tanımlar.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Ortam değişkenleri gibi geçerli kullanıcı tercihleri hakkında bilgiler içerir.|  
|<xref:Microsoft.Win32.Registry.DynData>|Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Yerel bilgisayar için yapılandırma verilerini tutan beş alt anahtar (donanım, SAM, güvenlik, yazılım ve sistem) içerir.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Yazılım bileşenleri için performans bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.Users>|Varsayılan Kullanıcı tercihleri hakkında bilgi içerir.|  
  
> [!IMPORTANT]
> Verileri yerel bilgisayara (<xref:Microsoft.Win32.Registry.LocalMachine>) göre geçerli kullanıcıya (<xref:Microsoft.Win32.Registry.CurrentUser>) yazmak daha güvenlidir. Oluşturmakta olduğunuz anahtar daha önce başka bir kötü amaçlı, büyük olasılıkla kötü amaçlı bir işlem tarafından oluşturulduğu zaman, genellikle "ele geçirme" olarak adlandırılan bir koşul oluşur. Bunun oluşmasını önlemek için, anahtar zaten yoksa `Nothing` döndüren <xref:Microsoft.Win32.RegistryKey.GetValue%2A>gibi bir yöntem kullanın.  
  
## <a name="reading-a-value-from-the-registry"></a>Kayıt defterinden bir değer okuma  

 Aşağıdaki kod, HKEY_CURRENT_USER bir dizenin nasıl okunacağını gösterir.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Aşağıdaki kod, HKEY_CURRENT_USER için bir dize okur, artırır ve yazar.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally Deyimi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Güvenlik ve Kayıt Defteri](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
