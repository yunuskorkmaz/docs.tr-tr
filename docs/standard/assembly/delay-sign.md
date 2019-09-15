---
title: Bir derlemeyi gecikmeli imzala
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: e7679520e246ab3eda03e6f0e0d092c7d09f1845
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991327"
---
# <a name="delay-sign-an-assembly"></a>Bir derlemeyi gecikmeli imzala

Bir kuruluş, geliştiricilerin günlük olarak erişebileceği, daha yakından korunan bir anahtar çiftine sahip olabilir. Ortak anahtar genellikle kullanılabilir, ancak özel anahtara erişim yalnızca birkaç bireyle kısıtlıdır. Tanımlayıcı adlara sahip derlemeler geliştirirken, tanımlayıcı adlı hedef derlemeye başvuran her derleme, hedef derlemeye tanımlayıcı bir ad vermek için kullanılan ortak anahtarın belirtecini içerir. Bu, geliştirme sürecinde ortak anahtarın kullanılabilir olmasını gerektirir.

Güçlü ad imzası için Taşınabilir çalıştırılabilir (PE) dosyasında alan ayırmak için derleme zamanında Gecikmeli veya kısmi imzalamayı kullanabilirsiniz, ancak genellikle derlemeyi teslim etmeden önce, daha sonraki bir aşamaya kadar gerçek imzalamayı erteleyebilirsiniz.

Bir derlemeyi gecikmeli imzalamak için:

1. Son imzalamayı sağlayacak olan kuruluştan anahtar çiftinin ortak anahtar bölümünü alın. Genellikle bu anahtar, Windows SDK tarafından belirtilen [tanımlayıcı ad Aracı (sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) kullanılarak oluşturulabilen bir *. snk* dosyası biçimindedir.

2. İki özel özniteliğe <xref:System.Reflection>sahip derleme için kaynak koda not ekleyin:

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, ortak anahtarı içeren dosyanın adını oluşturucuya bir parametre olarak geçirir.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>Bu, gecikme imzasının, oluşturucuya bir parametre olarak **doğru** geçirerek kullanıldığını gösterir.

   Örneğin:

   ```cpp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")];
   [assembly:AssemblyDelaySignAttribute(true)];
   ```

   ```csharp
   [assembly:AssemblyKeyFileAttribute("myKey.snk")]
   [assembly:AssemblyDelaySignAttribute(true)]
   ```

   ```vb
   <Assembly:AssemblyKeyFileAttribute("myKey.snk")>
   <Assembly:AssemblyDelaySignAttribute(True)>
   ```

3. Derleyici, ortak anahtarı derleme bildirimine ekler ve tam tanımlayıcı ad imzası için PE dosyasındaki alanı ayırır. Derleme derlenirken gerçek ortak anahtarın depolanması gerekir, bu derlemeye başvuran diğer derlemeler kendi derleme başvurusunda depolanacak anahtarı elde edebilir.

4. Derlemenin geçerli bir tanımlayıcı ad imzası olmadığından, bu imzanın doğrulanması kapatılmalıdır. Bunu, tanımlayıcı ad aracı ile **– VR** seçeneğini kullanarak yapabilirsiniz.

     Aşağıdaki örnek, *MyAssembly. dll*adlı bir derleme için doğrulamayı devre dışı bırakır.

   ```console
   sn –Vr myAssembly.dll
   ```

   Gelişmiş RıSC makinesi (ARM) mikro işlemciler gibi tanımlayıcı ad aracını çalıştıramıyorum platformlarda doğrulamayı devre dışı bırakmak için, **– VK** seçeneğini kullanarak bir kayıt defteri dosyası oluşturun. Kayıt defteri dosyasını, doğrulamayı kapatmak istediğiniz bilgisayarda kayıt defterine aktarın. Aşağıdaki örnek için `myAssembly.dll`bir kayıt defteri dosyası oluşturur.

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   **– VR** veya **– VK** seçeneği ile, isteğe bağlı olarak test anahtar imzalama için bir *. snk* dosyası ekleyebilirsiniz.

   > [!WARNING]
   > Güvenlik için tanımlayıcı adlara güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

   > [!NOTE]
   > Visual Studio ile geliştirme sırasında gecikme imzalamayı 64 bitlik bir bilgisayarda kullanırsanız ve **herhangi BIR CPU**için derleme derlerseniz, **-VR** seçeneğini iki kez uygulamanız gerekebilir. (Visual Studio 'da, **herhangi BIR CPU** **Platform hedefi** derleme özelliğinin bir değeridir; komut satırından derlerken varsayılan değerdir.) Uygulamanızı komut satırından veya dosya Gezgini 'nden çalıştırmak için, **-VR** seçeneğini derlemeye uygulamak için sn. exe ' nin 64 bit sürümünü kullanın [(tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md) . Tasarım zamanında derlemeyi Visual Studio 'ya yüklemek için (örneğin, derleme uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenleri içeriyorsa), güçlü ad aracının 32 bitlik sürümünü kullanın. Bunun nedeni, Just-In-Time (JıT) derleyicisi derlemeyi komut satırından çalıştırıldığında derlemeyi 64-bit yerel koda derlediğinde ve derleme tasarım zamanı ortamına yüklendiğinde, 32 bit yerel kodda.

5. Daha sonra, genellikle teslim etmeden hemen önce, derlemeyi kuruluşunuzun imza yetkilisine göndererek, tanımlayıcı ad aracı ile **– R** seçeneğini kullanarak gerçek tanımlayıcı ad imzalama.

   Aşağıdaki örnek, *MyAssembly. dll* adlı bir derlemeyi *sgKey. snk* anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Derlemeler oluştur](create.md)
- [Nasıl yapılır: Ortak özel anahtar çifti oluşturma](create-public-private-key-pair.md)
- [Sn. exe (tanımlayıcı ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Bütünleştirilmiş kod içeren program](program.md)
