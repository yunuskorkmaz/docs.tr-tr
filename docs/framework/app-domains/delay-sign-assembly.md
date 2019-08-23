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
ms.openlocfilehash: 17034eb5dcb48ae43b8e0cd0bd0f49d0b0920a8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921606"
---
# <a name="delay-signing-an-assembly"></a>Derleme İmzalamayı Geciktirme
Bir kuruluş, geliştiricilerin günlük olarak erişimi olmayan, daha yakından korunan bir anahtar çiftine sahip olabilir. Ortak anahtar genellikle kullanılabilir, ancak özel anahtara erişim yalnızca birkaç bireyle kısıtlıdır. Tanımlayıcı adlara sahip derlemeler geliştirirken, tanımlayıcı adlı hedef derlemeye başvuran her derleme, hedef derlemeye tanımlayıcı bir ad vermek için kullanılan ortak anahtarın belirtecini içerir. Bu, geliştirme sürecinde ortak anahtarın kullanılabilir olmasını gerektirir.  
  
 Güçlü ad imzası için Taşınabilir çalıştırılabilir (PE) dosyasında alan ayırmak için, oluşturma zamanında Gecikmeli veya kısmi imzalamayı kullanabilirsiniz, ancak daha sonraki bir aşamaya kadar (genellikle sadece derlemeyi teslim etmeden önce) gerçek imzalamayı erteleyebilirsiniz.  
  
 Aşağıdaki adımlarda, bir derlemeyi imzalamayı geciktir süreci ana hatlarıyla verilmiştir:  
  
1. Son imzalamayı sağlayacak kuruluştan anahtar çiftinin ortak anahtar bölümünü alın. Genellikle bu anahtar, Windows SDK tarafından belirtilen [tanımlayıcı ad Aracı (sn. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) kullanılarak oluşturulabilen bir. snk dosyası biçimindedir.  
  
2. İki özel özniteliğe <xref:System.Reflection>sahip derleme için kaynak koda not ekleyin:  
  
    - <xref:System.Reflection.AssemblyKeyFileAttribute>, ortak anahtarı içeren dosyanın adını oluşturucuya bir parametre olarak geçirir.  
  
    - <xref:System.Reflection.AssemblyDelaySignAttribute>Bu, gecikme imzasının, oluşturucuya bir parametre olarak **doğru** geçirerek kullanıldığını gösterir. Örneğin:  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3. Derleyici, ortak anahtarı derleme bildirimine ekler ve tam tanımlayıcı ad imzası için PE dosyasındaki alanı ayırır. Derleme derlenirken gerçek ortak anahtarın depolanması gerekir, bu derlemeye başvuran diğer derlemeler kendi derleme başvurusunda depolanacak anahtarı elde edebilir.  
  
4. Derlemenin geçerli bir tanımlayıcı ad imzası olmadığından, bu imzanın doğrulanması kapatılmalıdır. Bunu, tanımlayıcı ad aracı ile **– VR** seçeneğini kullanarak yapabilirsiniz.  
  
     Aşağıdaki örnek, adlı `myAssembly.dll`bir derleme için doğrulamayı devre dışı bırakır.  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     Gelişmiş RıSC makinesi (ARM) mikro işlemciler gibi tanımlayıcı ad aracını çalıştıramıyorum platformlarda doğrulamayı devre dışı bırakmak için, **– VK** seçeneğini kullanarak bir kayıt defteri dosyası oluşturun. Kayıt defteri dosyasını, doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterine aktarın. Aşağıdaki örnek için `myAssembly.dll`bir kayıt defteri dosyası oluşturur.  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     **– VR** veya **– VK** seçeneği ile, isteğe bağlı olarak test anahtar imzalama için bir. snk dosyası ekleyebilirsiniz.  
  
    > [!WARNING]
    > Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.
  
    > [!NOTE]
    > Visual Studio ile geliştirme sırasında gecikme imzalamayı 64 bitlik bir bilgisayarda kullanırsanız ve **herhangi BIR CPU**için derleme derlerseniz, **-VR** seçeneğini iki kez uygulamanız gerekebilir. (Visual Studio 'da, **herhangi BIR CPU** **Platform hedefi** derleme özelliğinin bir değeridir; komut satırından derlerken varsayılan değerdir.) Uygulamanızı komut satırından veya dosya Gezgini 'nden çalıştırmak için, **-VR** seçeneğini derlemeye uygulamak için sn. exe ' nin 64 bit sürümünü kullanın [(tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) . Tasarım zamanında derlemeyi Visual Studio 'ya yüklemek için (örneğin, derleme uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenleri içeriyorsa), güçlü ad aracının 32 bitlik sürümünü kullanın. Bunun nedeni, Just-In-Time (JıT) derleyicisi derlemeyi komut satırından çalıştırıldığında derlemeyi 64-bit yerel koda derlediğinde ve derleme tasarım zamanı ortamına yüklendiğinde, 32 bit yerel kodda.  
  
5. Daha sonra, genellikle teslim etmeden hemen önce, derlemeyi kuruluşunuzun imza yetkilisine göndererek, tanımlayıcı ad aracı ile **– R** seçeneğini kullanarak gerçek tanımlayıcı ad imzalama.  
  
     Aşağıdaki örnek, `sgKey.snk` anahtar çiftini kullanarak bir `myAssembly.dll` tanımlayıcı ad ile çağrılan bir derlemeyi imzalar.  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)
- [Nasıl yapılır: Ortak özel anahtar çifti oluşturma](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
