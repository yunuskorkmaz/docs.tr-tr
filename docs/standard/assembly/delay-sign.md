---
title: Derlemeyi gecikmeli imzalama
ms.date: 08/19/2019
helpviewer_keywords:
- deferring assembly signing
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, delaying assembly signing
- partial assembly signing
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 113df1ad3fc3ac1e27ebfef572494c1f15a3dbb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733168"
---
# <a name="delay-sign-an-assembly"></a>Derlemeyi gecikmeli imzalama

Bir kuruluş, geliştiricilerin günlük olarak erişemeyebileceği, sıkı korunan bir anahtar çiftine sahip olabilir. Ortak anahtar genellikle kullanılabilir, ancak özel anahtara erişim yalnızca birkaç kişiyle sınırlıdır. Güçlü adlara sahip derlemeler geliştirirken, güçlü adlandırılmış hedef derlemeye başvuran her derleme, hedef derlemeye güçlü bir ad vermek için kullanılan ortak anahtarın belirteci içerir. Bu, geliştirme işlemi sırasında ortak anahtarın kullanılabilir olmasını gerektirir.

Güçlü ad imzası için taşınabilir yürütülebilir (PE) dosyasında yer ayırmak için yapı zamanında gecikmeli veya kısmi imza kullanabilir, ancak gerçek imzayı genellikle derlemeyi göndermeden hemen önce, daha sonraki bir aşamaya erteleyebilirsiniz.

Bir derlemeyi geciktirmek için:

1. Anahtar çiftinin ortak anahtar kısmını, nihai imzalamayı yapacak kuruluştan alın. Genellikle bu anahtar, Windows SDK tarafından sağlanan Güçlü Ad aracı [(Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) kullanılarak oluşturulabilen bir *.snk* dosyası biçimindedir.

2. İki özel öznitelikleri ile derleme için kaynak <xref:System.Reflection>kodu açıklama:

   - <xref:System.Reflection.AssemblyKeyFileAttribute>, ortak anahtarı içeren dosyanın adını parametre olarak oluşturucuya geçirir.

   - <xref:System.Reflection.AssemblyDelaySignAttribute>, geciktirme imzalamanın, oluşturucuya bir parametre olarak **gerçek** olarak geçirilerek kullanıldığını gösterir.

   Örnek:

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

3. Derleyici ortak anahtarı derleme manifestosuna ekler ve tam güçlü ad imzası için PE dosyasına yer ayırır. Derleme oluşturulurken gerçek ortak anahtar depolanmalıdır, böylece bu derlemeye başvuran diğer derlemeler kendi derleme referanslarında depolanacak anahtarı elde edebilir.

4. Derlemede geçerli bir güçlü ad imzası olmadığından, imzanın doğrulanması kapatılmalıdır. Bunu Güçlü Ad aracıyla **-Vr** seçeneğini kullanarak yapabilirsiniz.

     Aşağıdaki örnek *myAssembly.dll*adlı bir derleme için doğrulamayı kapatır.

   ```console
   sn –Vr myAssembly.dll
   ```

   Gelişmiş RISC Machine (ARM) mikroişlemcileri gibi Güçlü Ad aracını çalıştıramadığınız platformlarda doğrulamayı kapatmak için bir kayıt defteri dosyası oluşturmak için **-Vk** seçeneğini kullanın. Kayıt defteri dosyasını doğrulamayı kapatmak istediğiniz bilgisayardaki kayıt defterine aktarın. Aşağıdaki örnek için `myAssembly.dll`bir kayıt defteri dosyası oluşturur.

   ```console
   sn –Vk myRegFile.reg myAssembly.dll
   ```

   **-Vr** veya **-Vk** seçeneği ile isteğe bağlı olarak test anahtarı imzalama için bir *.snk* dosyası ekleyebilirsiniz.

   > [!WARNING]
   > Güvenlik için güçlü isimlere güvenmeyin. Yalnızca benzersiz bir kimlik sağlarlar.

   > [!NOTE]
   > Visual Studio ile geliştirme sırasında 64 bit bilgisayarda gecikme imzalamayı kullanırsanız ve Herhangi bir **CPU**için bir derleme derlerseniz, **-Vr** seçeneğini iki kez uygulamanız gerekebilir. (Visual Studio'da, Herhangi bir **CPU** **Platform Hedef** yapı özelliğinin bir değeridir; komut satırından derlediğinizde varsayılandır.) Uygulamanızı komut satırından veya Dosya Gezgini'nden çalıştırmak **için, -Vr** seçeneğini derlemeye uygulamak için [Sn.exe'nin (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md) 64 bit sürümünü kullanın. Derlemeyi tasarım zamanında Visual Studio'ya yüklemek için (örneğin, montaj uygulamanızdaki diğer derlemeler tarafından kullanılan bileşenler içeriyorsa), güçlü ad aracının 32 bit sürümünü kullanın. Bunun nedeni, derleme komut satırından çalıştırıldığında derlemeyi 64 bit yerel koda ve derleme tasarım zamanı ortamına yüklendiğinde 32 bit yerel koda derlemesidir.

5. Daha sonra, genellikle sevkiyattan hemen önce, derlemeyi Güçlü Ad aracıyla **–R** seçeneğini kullanarak gerçek güçlü ad imzalama için kuruluşunuzun imzalama yetkisine gönderirsiniz.

   Aşağıdaki örnek, *sgKey.snk* anahtar çiftini kullanarak güçlü bir adla *myAssembly.dll* adlı bir derlemeyi imzalar.

   ```console
   sn -R myAssembly.dll sgKey.snk
   ```

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme oluşturma](create.md)
- [Nasıl yapilir: Genel-özel anahtar çifti oluşturma](create-public-private-key-pair.md)
- [Sn.exe (Güçlü Ad aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
