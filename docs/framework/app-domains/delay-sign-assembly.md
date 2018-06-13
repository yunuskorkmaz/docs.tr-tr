---
title: Derleme İmzalamayı Geciktirme
ms.date: 07/31/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4457bd6d5efd7404cdba6c5fbdbffa9f9eb62141
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743996"
---
# <a name="delay-signing-an-assembly"></a>Derleme İmzalamayı Geciktirme
Bir kuruluş, geliştiricilerin günlük olarak için erişimi yoktur yakından korumalı bir anahtar çifti olabilir. Ortak anahtar genellikle kullanılabilir, ancak özel anahtar erişimi yalnızca birkaç kişi sınırlıdır. Derlemeleri tanımlayıcı adlar ile geliştirirken, her derleme bu başvurular tanımlayıcı adlı hedef derlemeyi hedef derleme güçlü bir ad vermek için kullanılan ortak anahtar belirteci içeriyor. Bu, ortak anahtar geliştirme işlemi sırasında kullanılabilir olması gerekir.  
  
 Ayrılmış alanı dosyasındaki taşınabilir yürütülebilir (PE) sağlam ad imzası, ancak gerçek imzalama (derleme göndermeden önce genellikle yalnızca) bazı sonraki aşaması kadar erteleme gecikmeli ya da kısmi derleme zamanında imzalama kullanabilirsiniz.  
  
 Aşağıdaki adımları gecikme oturum bütünleştirilmiş sürecini özetlemektedir:  
  
1.  Anahtar çiftini ortak anahtar kısmını nihai imzalama yapan kuruluşlardan. Genellikle bu anahtarı kullanılarak oluşturulan bir .snk dosya biçimindedir [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Kaynak kodu derleme iki özel öznitelikleri için ek açıklama <xref:System.Reflection>:  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, kendi oluşturucusunu bir parametre olarak genel anahtarını içeren dosyanın adını geçirir.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, bu gecikme imzalama belirten geçirerek kullanılıyor **true** kurucusu parametre olarak. Örneğin:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Derleyici derleme bildirimine ortak anahtar ekler ve tam sağlam ad imzası PE dosyasında alan ayırır. Bu derleme başvurusu diğer derlemelerden kendi derleme başvurusu'nda depolamak için anahtar alabilmesi adına, derlemeyi sırada gerçek ortak anahtarı depolanması gerekir.  
  
4.  Derleme geçerli sağlam ad imzası sahip olmadığından, bu imza doğrulaması kapatılması gerekir. Kullanarak bunu yapabilirsiniz **– Vr** tanımlayıcı ad aracı seçeneğiyle.  
  
     Doğrulama adlı bir derleme için aşağıdaki örneği kapatır `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Gelişmiş RISC makinesi (ARM) mikro gibi tanımlayıcı ad aracı çalıştırdığı olamaz doğrulama platformlarda devre dışı bırakmak üzere kullanmak **– Vk** seçeneği kayıt defteri dosyası oluşturun. Kayıt defteri dosyasını doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterini alın. Aşağıdaki örnek için bir kayıt defteri dosyası oluşturur `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Ya da ile **– Vr** veya **– Vk** seçeneği, isteğe bağlı olarak test anahtar imzalama için bir .snk dosyası içerebilir.  
  
    > [!WARNING]
    > Güvenlik tanımlayıcı adlar kullanmayın. Yalnızca benzersiz bir kimlik sağlarlar.
  
    > [!NOTE]
    >  Bir 64-bit bilgisayarda Visual Studio ile geliştirme sırasında imzalamayı geciktirme kullanırsanız ve bir derleme için derleme **herhangi bir CPU**, uygulanacak olabilir **- Vr** iki kez seçeneği. (Visual Studio'da **herhangi bir CPU** bir değeri **Platform hedefi** özelliği yapı; komut satırından derlerken varsayılan değer.) Komut satırından veya dosya Gezgini'nden uygulamanızı çalıştırmak için 64-bit sürümünü kullanmanız [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) uygulamak için **- Vr** derleme seçeneği. (Örneğin, derleme, uygulamanızda diğer derlemeleri tarafından kullanılan bileşenleri içeriyorsa) tasarım zamanında Visual Studio'ya derlemeyi yüklemek için tanımlayıcı ad aracı 32-bit sürümünü kullanın. Tasarım zamanı ortamına derleme yüklendiğinde tam zamanında (JIT) derleyici komut satırından derleme çalıştırdığınızda yerel kod 64-bit ve 32-bit yerel kodu derleme derler olmasıdır.  
  
5.  Daha sonra genellikle tam sevkiyat önce kuruluşunuz derlemeye kullanarak imzalama gerçek güçlü ad için yetkili imzalama gönderme **– R** tanımlayıcı ad aracı seçeneğiyle.  
  
     Aşağıdaki örnek olarak adlandırılan bir derlemeyi imzalar `myAssembly.dll` kullanarak bir güçlü ad ile `sgKey.snk` anahtar çifti.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
