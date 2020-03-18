---
title: 'Nasıl yapilir: Genel-özel anahtar çifti oluşturma'
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8a9845e3cd18ff86ec04216ad0e9c5606186b113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73122526"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Nasıl yapilir: Genel-özel anahtar çifti oluşturma

Güçlü bir ada sahip bir derlemeyi imzalamak için ortak/özel anahtar çiftiniz olmalıdır. Bu ortak ve özel şifreleme anahtar çifti derleme sırasında güçlü adlandırılmış bir derleme oluşturmak için kullanılır. [Güçlü Ad aracını (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md)kullanarak bir anahtar çifti oluşturabilirsiniz. Anahtar çifti dosyaları genellikle bir *.snk* uzantısı vardır.

> [!NOTE]
> Visual Studio'da, C# ve Visual Basic proje özelliği sayfaları, varolan anahtar dosyalarını seçmenizi veya *Sn.exe'yi*kullanmadan yeni anahtar dosyaları oluşturmanızı sağlayan bir **İmzalama** sekmesi içerir. Visual C++'da, **Özellik Sayfaları** penceresinin **Yapılandırma Özellikleri** bölümünün **Bağlayıcı** bölümünde **Gelişmiş** özellik sayfasında varolan bir anahtar dosyasının konumunu belirtebilirsiniz. Anahtar dosya <xref:System.Reflection.AssemblyKeyFileAttribute> çiftlerini tanımlamak için özniteliğin kullanımı Visual Studio 2005 ile başlayan eski haline getirilmiştir.

## <a name="create-a-key-pair"></a>Anahtar çifti oluşturma

Bir komut isteminde bir anahtar çifti oluşturmak için aşağıdaki komutu yazın:

**sn –k** \< *dosya adı*>

Bu komutta, *dosya adı* anahtar çiftini içeren çıktı dosyasının adıdır.

Aşağıdaki *örneksgKey.snk*adlı bir anahtar çifti oluşturur.

```cmd
sn -k sgKey.snk
```

Bir derlemeyi imzalamayı geciktirmek istiyorsanız ve tüm anahtar çiftini denetlerseniz (test senaryoları dışında olası değildir), anahtar çifti oluşturmak için aşağıdaki komutları kullanabilir ve ardından ortak anahtarı ayrı bir dosyaya ayıklayabilirsiniz. İlk olarak, anahtar çiftini oluşturun:

```cmd
sn -k keypair.snk
```

Ardından, ortak anahtarı anahtar çiftinden ayıklayın ve ayrı bir dosyaya kopyalayın:

```cmd
sn -p keypair.snk public.snk
```

Anahtar çiftini oluşturduktan sonra, dosyayı güçlü ad imzalama araçlarının bulabileceği bir yere koymanız gerekir.

Güçlü bir ada sahip bir derleme imzalarken, [Derleme Bağlayıcısı (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) anahtar dosyasını geçerli dizine ve çıktı dizine göre arar. Komut satırı derleyicilerini kullanırken, kod modüllerinizi içeren geçerli dizinin anahtarını kopyalayabilirsiniz.

Visual Studio'nun proje özelliklerinde **İmza** sekmesi olmayan önceki bir sürümünü kullanıyorsanız, önerilen anahtar dosyası konumu aşağıdaki gibi belirtilen dosya özniteliği içeren proje dizinidir:

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
