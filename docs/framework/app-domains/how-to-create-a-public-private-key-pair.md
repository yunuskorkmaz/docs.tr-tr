---
title: 'Nasıl yapılır: genel-özel anahtar çifti oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08715f2824dcb7dbc2c6aa26fd3bd8bd71b97038
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779234"
---
# <a name="how-to-create-a-public-private-key-pair"></a>Nasıl yapılır: genel-özel anahtar çifti oluşturma

Bir derlemeyi katı bir adla imzalamak için ortak/özel anahtar çifti olmalıdır. Bu ortak ve özel şifreleme anahtar çifti, derleme sırasında bir tanımlayıcı adlı bütünleştirilmiş kod oluşturmak için kullanılır. Anahtar çiftini kullanarak oluşturabileceğiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md). Anahtar çifti dosyaları .snk uzantı genellikle sahiptir.

> [!NOTE]
> Visual Studio'da C# ve Visual Basic proje özellik sayfaları dahil bir **imzalama** sağlar, mevcut anahtar dosya seçin veya Sn.exe kullanmadan yeni anahtar dosyaları oluşturmak için sekmesinde. Visual C++'da, mevcut bir anahtar dosyasının konumunu belirtebilirsiniz **Gelişmiş** özellik sayfasında **bağlayıcı** bölümünü **yapılandırma özellikleri** bölümü **Özellik sayfaları** penceresi. Kullanımını <xref:System.Reflection.AssemblyKeyFileAttribute> anahtar dosyası çifti tanımlamak için öznitelik Visual Studio 2005 ve sonraki eski sürümlerinde hale getirilmiştir.

## <a name="to-create-a-key-pair"></a>Bir anahtar çifti oluşturmak için

1.  Komut satırında, aşağıdaki komutu yazın:

     **sn – k** \< *dosya adı*>

     Bu komutta *dosya adı* anahtar çiftini içeren çıkış dosyasının adı.

 Aşağıdaki örnekte adlı bir anahtar çifti oluşturur `sgKey.snk`.

```
sn -k sgKey.snk
```

 Bir anahtar çifti oluşturmak ve ardından ortak anahtarı bundan farklı bir dosyaya ayıklamak için derlemeyi imzala geciktirmek istediğinize ve (hangi test senaryoları dışında düşüktür) tüm anahtar çiftini denetlemek, kullanabileceğiniz aşağıdaki komutları. İlk olarak, bir anahtar çifti oluşturun:

```
sn -k keypair.snk
```

 Ardından, anahtar çiftinden ortak anahtarı ayıklar ve ayrı bir dosyaya kopyalayın:

```
sn -p keypair.snk public.snk
```

 Anahtar çiftini oluşturduktan sonra kesin ad imzalama araçları, nerede bulabileceğiniz bir dosya yerleştirmeniz gerekir.

 Bir derlemeyi katı bir adla imzalarken [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) geçerli dizin ve çıkış dizini göreli dosya anahtar arar. Komut satırı derleyicilerini kullanırken anahtarı kod modüllerinizi içeren geçerli dizine yalnızca kopyalayabilirsiniz.

 Olmayan Visual Studio'nun önceki bir sürümü kullanıyorsanız, bir **imzalama** sekmesini Proje Özellikleri'nde proje dizini gibi belirtilen dosya özniteliği ile önerilen anahtar dosyası konumudur:

 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]

## <a name="see-also"></a>Ayrıca Bkz.

- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
