---
description: Güvenlik için C# derleyici seçenekleri. Thee seçenekleri, imzalama derlemelerini veya adres alanı yerleşimini denetler.
title: C# derleyici seçenekleri-güvenlik seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- PublicSign compiler option [C#]
- DelaySign compiler option [C#]
- KeyFile compiler option [C#]
- KeyContainer compiler option [C#]
- HighEntropyVA compiler option [C#]
ms.openlocfilehash: db7b612fa2e4ddb566ac2ba5ef9e4e66c5f0b0ab
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482902"
---
# <a name="c-compiler-options-for-security-options"></a>Güvenlik seçenekleri için C# derleyici seçenekleri

Aşağıdaki seçenekler derleyici güvenlik seçeneklerini denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **Publicsign**  /  `-publicsign` : derlemeyi herkese açık olarak imzalayın.
- **Delaysign**  /  `-delaysign` : tanımlayıcı ad anahtarının yalnızca ortak kısmını kullanarak derlemeyi gecikmeli imzala.
- **Anahtar dosyası**  /  `-keyfile` : Tanımlayıcı ad anahtar dosyası belirtin.
- **Keycontainer**  /  `-keycontainer` : tanımlayıcı ad anahtar kapsayıcısı belirtin.
- **Highentropyva**  /  `-highentropyva` : yüksek entropi adres alanı düzeni rastgele seçme (ASLR) özelliğini etkinleştirin

## <a name="publicsign"></a>PublicSign

Bu seçenek derleyicinin ortak anahtar uygulamasına, ancak derlemeyi gerçekten imzalamasına neden olur. **Publicsign** seçeneği Ayrıca, çalışma zamanına dosyanın imzalandığını bildiren derlemede bir bit belirler.

```xml
<PublicSign>true</PublicSign>
```

**Publicsign** seçeneği, [**keyfile**](#keyfile) veya [**keycontainer**](#keycontainer) seçeneğinin kullanılmasını gerektirir. **KeyFile** ve **keycontainer** seçenekleri ortak anahtarı belirtir. **Publicsign** ve **publicsign** seçenekleri birbirini dışlıyor. Bazen "sahte imza" veya "OSS işareti" olarak adlandırılan ortak imzalama, çıkış derlemesinde ortak anahtarı içerir ve "imzalanmış" bayrağını ayarlar. Ortak imzalama aslında özel anahtarla derlemeyi imzalayamıyor. Geliştiriciler açık kaynaklı projeler için genel işareti kullanır.  Kişiler, derlemeleri imzalamak için kullanılan özel anahtara erişime sahip olmadıkları zaman yayınlanan "tamamen imzalanmış" derlemeleriyle uyumlu derlemeler oluşturur. Genellikle derlemenin tamamen imzalanıp imzalanmadığını kontrol etmek gerektiğinden, genel olarak oluşturulan bu derlemeler neredeyse her bir senaryoda, tam olarak imzalanan bir şekilde kullanılabilir.

## <a name="delaysign"></a>DelaySign

Bu seçenek derleyicinin çıkış dosyasında alan ayırmasını sağlayarak bir dijital imzanın daha sonra eklenebilmesini sağlar.

```xml
<DelaySign>true</DelaySign>
```

Tam olarak imzalanan bir derlemeyi istiyorsanız **delaysign** kullanın. Yalnızca ortak anahtarı derlemeye yerleştirmek istiyorsanız **delaysign** kullanın. , [**Keyfile**](#keyfile) veya [**keycontainer**](#keycontainer)Ile kullanılmadığı müddetçe **delaysign** seçeneğinin hiçbir etkisi yoktur. [**Keycontainer**](#keycontainer) ve [**publicsign**](#publicsign) seçenekleri birbirini dışlıyor. Tam olarak imzalanan bir derleme istediğinizde, derleyici bildirimi içeren dosyayı (derleme meta verileri) karma hale getirir ve bu karmayı özel anahtarla imzalar. Bu işlem, bildirimi içeren dosyada depolanan bir dijital imza oluşturur. Bir derlemenin gecikmesi gecikmeli kaydolduğunda, derleyici imzayı hesaplamaz ve depolamaz. Bunun yerine, derleyici daha sonra eklenebilmesi için dosyada alanı ayırır.

**Delaysign** kullanılması, bir sınayıcı 'ın derlemeyi genel önbellekte almasına izin verir. Test ettikten sonra, derleme [bağlayıcı](../../../framework/tools/al-exe-assembly-linker.md) yardımcı programını kullanarak özel anahtarı derlemeye yerleştirerek derlemeyi tamamen imzalayabilirsiniz. Daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).

## <a name="keyfile"></a>Dosyasına

Şifreleme anahtarını içeren dosya adını belirtir.

```xml
<KeyFile>filename</KeyFile>
```

`file` , tanımlayıcı ad anahtarını içeren dosyanın adıdır. Bu seçenek kullanıldığında, derleyici belirtilen dosyadan ortak anahtarı derleme bildirimine ekler ve ardından son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. [**-Target: Module**](output.md#targettype)ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve [**AddModules**](inputs.md#addmodules)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir. Ayrıca, bir şifreleme bilgilerinizi, [**keycontainer**](#keycontainer)ile derleyiciye geçirebilirsiniz. Kısmen imzalanmış bir derleme istiyorsanız [**delaysign**](#delaysign) kullanın. Aynı derlemede hem **keyfile** hem de **keycontainer** belirtilirse, derleyici ilk olarak anahtar kapsayıcısını dener. Bu başarılı olursa, derleme anahtar kapsayıcısındaki bilgilerle imzalanır. Derleyici anahtar kapsayıcısını bulamazsa, [**keyfile**](#keyfile)ile belirtilen dosyayı dener. Bu başarılı olursa, derleme anahtar dosyasındaki bilgilerle imzalanır ve anahtar bilgileri anahtar kapsayıcısına yüklenir. Sonraki derlemede, anahtar kapsayıcısı geçerli olacaktır. Anahtar dosyası yalnızca ortak anahtar içerebilir. Daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).

## <a name="keycontainer"></a>KeyContainer

Şifreleme anahtarı kapsayıcısının adını belirtir.

```xml
<KeyContainer>container</KeyContainer>
```

`container` , tanımlayıcı ad anahtar kapsayıcısının adıdır. **Keycontainer** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur. Derleyici, belirtilen kapsayıcıdan derleme bildirimine ortak bir anahtar ekler ve son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. `sn -i` anahtar çiftini bir kapsayıcıya kurar. Derleyici CoreCLR üzerinde çalıştırıldığında bu seçenek desteklenmez. CoreCLR üzerinde oluşturma sırasında bir derlemeyi imzalamak için, [**keyfile**](#keyfile) seçeneğini kullanın. [**TargetType**](output.md#targettype)ile derlerseniz, anahtar dosyasının adı modülde tutulur ve bu modülü [**AddModules**](inputs.md#addmodules)içeren bir derlemede derlerken derlemeye dahil edilir. Bu seçeneği, <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType> herhangi bir Microsoft ara dili (MSIL) modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz. Ayrıca, [**anahtar**](#keyfile)anahtarlarla şifreleme bilgilerinizi derleyiciye geçirebilirsiniz. Ortak anahtarı derleme bildirimine eklemek, ancak test edilene kadar derlemeyi imzalamak için [**delaysign**](#delaysign) kullanın. Daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).

## <a name="highentropyva"></a>HighEntropyVA

**Highentropyva** derleyici seçeneği Windows çekirdeğine, belirli bir yürütülebilir dosyanın yüksek entropi adres alanı düzeni rastgele SEÇIMINI (ASLR) destekleyip desteklemediğini söyler.

```xml
<HighEntropyVA>true</HighEntropyVA>
```

Bu seçenek, 64 bitlik bir yürütülebilir dosyanın veya [**PlatformTarget**](output.md#platformtarget) derleyici seçeneği tarafından işaretlenen bir yürütülebilir dosyanın yüksek bir entropi sanal adres alanını desteklediğini belirtir. Seçenek varsayılan olarak devre dışıdır. Etkinleştirmek için **highentropyva** kullanın.

**Highentropyva** seçeneği, Windows çekirdeğinin uyumlu sürümlerinin ASLR bir parçası olarak bir işlemin adres alanı yerleşimini rastgele hale getirmek için daha yüksek bir entropi kullanmasına olanak sağlar. Daha yüksek serbestlik derecenin kullanılması, yığınlar ve yığınların gibi bellek bölgelerine daha fazla sayıda adresin ayrılabileceği anlamına gelir. Sonuç olarak, belirli bir bellek bölgesinin konumunu tahmin etmek daha zordur. **Highentropyva** derleyici seçeneği, hedef yürütülebiliri gerektirir ve bağımlı olduğu tüm modüller 64 bitlik bir işlem olarak çalışırken 4 GIGABAYTTAN (GB) daha büyük işaretçi değerlerini işleyebilir.
