---
title: Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 10431b1ad40ed320541a22fb46cc8db6dbb775b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360078"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma (Visual Basic)

, `My.Computer.Registry` Kayıt defterine karşı programlama yaparken temel ihtiyaçlarınızı kapsamalıdır, ancak <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> .NET Framework ad alanındaki ve sınıflarını da kullanabilirsiniz <xref:Microsoft.Win32> .  
  
## <a name="keys-in-the-registry-class"></a>Kayıt defteri sınıfındaki anahtarlar  

 <xref:Microsoft.Win32.Registry>Sınıfı, alt anahtarlara ve değerlerine erişmek için kullanılabilen temel kayıt defteri anahtarlarını sağlar. Temel anahtarlar salt okunurdur. Aşağıdaki tabloda, sınıfının açığa çıkarılan yedi anahtar listelenmektedir ve açıklanmaktadır <xref:Microsoft.Win32.Registry> .  
  
|**Anahtar**|**Açıklama**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Belge türlerini ve bu türlerle ilişkili özellikleri tanımlar.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Kullanıcıya özgü olmayan donanım yapılandırma bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Ortam değişkenleri gibi geçerli kullanıcı tercihleri hakkında bilgiler içerir.|  
|<xref:Microsoft.Win32.Registry.DynData>|Sanal cihaz sürücüleri tarafından kullanılan gibi dinamik kayıt defteri verileri içerir.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Yerel bilgisayar için yapılandırma verilerini tutan beş alt anahtar (donanım, SAM, güvenlik, yazılım ve sistem) içerir.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Yazılım bileşenleri için performans bilgilerini içerir.|  
|<xref:Microsoft.Win32.Registry.Users>|Varsayılan Kullanıcı tercihleri hakkında bilgi içerir.|  
  
> [!IMPORTANT]
> Geçerli kullanıcıya () yerel bilgisayardan () veri yazmak daha güvenlidir <xref:Microsoft.Win32.Registry.CurrentUser> <xref:Microsoft.Win32.Registry.LocalMachine> . Oluşturmakta olduğunuz anahtar daha önce başka bir kötü amaçlı, büyük olasılıkla kötü amaçlı bir işlem tarafından oluşturulduğu zaman, genellikle "ele geçirme" olarak adlandırılan bir koşul oluşur. Bunun oluşmasını önlemek için, <xref:Microsoft.Win32.RegistryKey.GetValue%2A> anahtar zaten yoksa, gibi bir yöntemi kullanın `Nothing` .  
  
## <a name="reading-a-value-from-the-registry"></a>Kayıt defterinden bir değer okuma  

 Aşağıdaki kod, HKEY_CURRENT_USER bir dizenin nasıl okunacağını gösterir.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Aşağıdaki kod, HKEY_CURRENT_USER için bir dize okur, artırır ve yazar.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally Deyimi](../../../language-reference/statements/try-catch-finally-statement.md)
- [Kayıt Defterinden Okuma ve Kayıt Defterine Yazma](reading-from-and-writing-to-the-registry.md)
- [Güvenlik ve Kayıt Defteri](security-and-the-registry.md)
