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
ms.openlocfilehash: a833bb0f412407d1f18793c356d4c207716eb101
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632627"
---
# <a name="delay-signing-an-assembly"></a>Derleme İmzalamayı Geciktirme
Bir kuruluş geliştiricileri her gün için erişimi yoktur yakından korumalı bir anahtar çifti olabilir. Genellikle ortak anahtarı mevcut ancak özel anahtarına erişime yalnızca birkaç kişilerle sınırlıdır. Derlemeleri tanımlayıcı adlarla geliştirirken, her derleme başvuruları tanımlayıcı adlı hedef derlemeye hedef derleme tanımlayıcı bir ad vermek için kullanılan ortak anahtar belirtecini içerir. Bu ortak anahtarı geliştirme sürecinde kullanılabilir olmasını gerektirir.  
  
 Taşınabilir yürütülebilir (PE) dosyanın tanımlayıcı ad imzası için alan ayırmak, ancak gerçek imzalama bazı (derleme göndermeden önce genellikle yalnızca) sonraki aşama kadar erteleme, geciken ya da kısmi derleme zamanında imzalama'ı kullanabilirsiniz.  
  
 Aşağıdaki adımlar, bir derlemeyi gecikmeli imza işleme özetlemektedir:  
  
1.  Anahtar çiftinden ortak anahtar kısmını nihai imzalama işlemi gerçekleştirecek kuruluşlardan. Genellikle bu anahtarı kullanılarak oluşturulan bir .snk dosyası biçiminde olan [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) tarafından sağlanan [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
2.  Kaynak kodu derlemeyi iki özel öznitelikleri ile için ek açıklama <xref:System.Reflection>:  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute>, oluşturucusuna bir parametre olarak ortak anahtarı içeren dosyanın adını geçirir.  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute>, söz konusu Gecikmeli imzalama gösteren geçirerek kullanılıyor **true** oluşturucusuna bir parametre olarak. Örneğin:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  Derleyici ortak anahtarı derleme bildirimine ekler ve PE dosyasının tam tanımlayıcı ad imzası için alan ayırır. Bu derlemeye başvuran diğer derlemeler, kendi derleme başvurusu depolamak için anahtar alabilmesi derlemeyi sırada gerçek ortak anahtarı depolanmalıdır.  
  
4.  Derleme geçerli bir tanımlayıcı ad imzası olmadığından, bu imza doğrulaması kapatılması gerekir. Kullanarak bunu yapabilirsiniz **– Vr** tanımlayıcı ad aracı seçeneği.  
  
     Aşağıdaki örnekte adlı bir derleme için doğrulama kapatır `myAssembly.dll`.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Tanımlayıcı ad aracı gibi gelişmiş RISC makinesi (ARM) mikro çalıştırdığı olamaz platformları doğrulamayı kapatmak için kullanmak **– Vk** seçeneği kayıt defteri dosyası oluşturun. Kayıt defteri dosyasını doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterini alın. Aşağıdaki örnek için bir kayıt defteri dosyası oluşturur `myAssembly.dll`.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     Ya da ile **– Vr** veya **– Vk** seçeneği, isteğe bağlı olarak test anahtar imzalamak için bir .snk dosyası içerebilir.  
  
    > [!WARNING]
    > Güvenlik için tanımlayıcı adlar güvenmeyin. Benzersiz bir kimliğe sağlarlar.
  
    > [!NOTE]
    >  Bir 64 bit bilgisayarda Visual Studio ile geliştirme sırasında imzalamayı geciktirme kullanıyorsanız ve bir derleme için derleme **herhangi bir CPU**, uygulamak gerekebilir **- Vr** iki kez seçeneği. (Visual Studio'da **herhangi bir CPU** bir değeri **Platform hedefi** özellik oluşturun; varsayılan olarak, komut satırından derlerken, etkin.) Komut satırından veya dosya Gezgini'nden uygulamanızı çalıştırmak için 64 bit sürümünü kullanan [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) uygulanacak **- Vr** derleme seçeneği. (Örneğin, uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenleri derlemeyi içeren) tasarım zamanında, Visual Studio'ya derlemeyi yüklemek için tanımlayıcı ad Aracı'nın 32-bit sürümü kullanın. Derleme tasarım zamanı ortamına yüklendiğinde, just-ın-time (JIT) derleyici derleme komut satırından çalıştırdığınızda yerel kod 64-bit ve 32 bit yerel kod için derleme derler olmasıdır.  
  
5.  Daha sonra genellikle tam aktarmadan önce kuruluşunuz derlemeye projenin yetkilisi kullanarak imzalama gerçek tanımlayıcı ad imzalama gönderme **– R** tanımlayıcı ad aracı seçeneği.  
  
     Aşağıdaki örnek olarak adlandırılan bir derlemeyi imzalar `myAssembly.dll` kullanarak bir tanımlayıcı ad ile `sgKey.snk` anahtar çifti.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)
- [Nasıl yapılır: Genel-özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
