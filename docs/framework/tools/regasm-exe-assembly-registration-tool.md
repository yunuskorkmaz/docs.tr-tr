---
title: Regasm.exe (Derleme Kayıt Aracı)
description: Regasm.exe, derleme kayıt aracını kullanın. Derleme meta verilerini okuyun ve gerekli girdileri kayıt defterine ekleyerek COM istemcilerinin .NET sınıfları oluşturmasına izin verir.
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
ms.openlocfilehash: a3af6a0fbc7c9c695e18448da285977f04fd72ef
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517262"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (Derleme Kayıt Aracı)

Derleme Kayıt aracı, derleme içindeki meta verileri okur ve kayıt defterine gerekli girişleri ekler, bu da COM istemcilerinin şeffaf olarak .NET Framework sınıfları oluşturmalarına izin verir. Sınıf kaydettirildikten sonra, COM istemcileri artık sınıfı bir COM sınıfıymış gibi kullanabilir. Sınıf yalnızca bir defa, derleme yüklenirken kaydettirilir. Derleme içindeki sınıf örnekleri gerçekten kaydettirilene kadar COM'dan oluşturulamaz.

Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Söz dizimi

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Parametreler

|Parametre|Açıklama|
|---------------|-----------------|
|*assemblyFile & lt*|COM ile kaydettirilecek derleme.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/CodeBase**|Kayıt defterinde bir Kod Temeli girişi oluşturur. Codebase girişi, genel derleme önbelleğinde yüklü olmayan bir derlemenin dosya yolunu belirtir. Kayıt yaptığınız derlemeyi daha sonra genel derleme önbelleğine yükleyeceksiniz bu seçeneği belirtmeyin. **/CODEBASE** seçeneği Ile belirttiğiniz *assemblyFile* bağımsız değişkeni, [tanımlayıcı adlı bir derleme](../../standard/assembly/strong-named.md)olmalıdır.|
|**/Registered**|Bu aracın yalnızca zaten kayıtlı durumdaki tür kitaplıklarına başvuracağını belirtir.|
|**/asmpath: Dizin**|Derleme başvuruları içeren bir dizini belirtir. , **/Regfile** seçeneği ile birlikte kullanılmalıdır.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/regfile** [**:** *regfile*]|Gerekli kayıt defteri girdilerini içeren derleme için belirtilen .reg dosyasını oluşturur. Bu seçeneği belirtmek kayıt defterini değiştirmez. Bu seçeneği **/u** veya **/tlb** seçenekleriyle birlikte kullanamazsınız.|
|**/Silent** veya **/s**|Başarı iletilerinin görüntülenmesini bastırır.|
|**/tlb** [**:** *TypeLibFile*]|Belirtilen derlemeden, derleme içinde tanımlanmış erişilebilir türlerin tanımlarını içeren bir tür kitaplığı oluşturur.|
|**/Unregister** veya **/u**|*AssemblyFile*içinde bulunan oluşturulabilir sınıflarının kaydını siler. Bu seçeneği kullanmamak, Regasm.exe'nin derlemedeki oluşturulabilir sınıfları kaydettirmesine neden olur.|
|**/verbose**|Ayrıntılı modu belirtir; bir tür kitaplığının oluşturulması gereken, **/tlb** seçeneğiyle belirtildiğinde, başvurulan derlemelerin bir listesini görüntüler.|
|**/?** veya **/help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

> [!NOTE]
> Regasm.exe komut satırı seçenekleri büyük/küçük harfe duyarsızdır. Seçeneğin, yalnızca onu benzersiz şekilde tanımlamaya yetecek kadarını sağlamanız yeterlidir. Örneğin, **/n** , **/nologo** ile eşdeğerdir ve **/t:** *çıkışdosyası. tlb* , **/tlb:** *çıkışdosyası. tlb*ile eşdeğerdir.

## <a name="remarks"></a>Açıklamalar

Değişiklikleri doğrudan kayıt defterine getirmek yerine kayıt defteri girdilerini içeren bir. reg dosyası oluşturmak için **/regfile** seçeneğini kullanabilirsiniz. Kayıt Defteri Düzenleyicisi (Regedit.exe) aracı ile .reg dosyasını içe aktararak, bir bilgisayarda kayıt defterini güncelleştirebilirsiniz. . Reg dosyası, Kullanıcı tanımlı yazmaç işlevleri tarafından yapılabilecek bir kayıt defteri güncelleştirmesi içermiyor. **/Regfile** seçeneği yalnızca yönetilen sınıfların kayıt defteri girdilerini yayar. Bu seçenek `TypeLibID` s veya s girdilerini göstermez `InterfaceID` .

**/Tlb** seçeneğini belirttiğinizde, Regasm.exe derlemede bulunan türleri açıklayan bir tür kitaplığı oluşturur ve kaydettirir. RegAsm.exe oluşturulan tür kitaplıklarını geçerli çalışma dizinine veya çıktı dosyası için belirtilen dizine yerleştirir. Diğer derlemelere başvuran bir derleme için tür kitaplığı oluşturmak, bazı tür kitaplıklarının tek seferde oluşturulmasına neden olabilir. Visual Studio gibi geliştirme araçlarına tür bilgilerini sağlamak için tür kitaplığını kullanabilirsiniz. Kaydolduğunuz derleme tür kitaplığı alma programı ([Tlbimp.exe](tlbimp-exe-type-library-importer.md)) tarafından üretildiyse **/tlb** seçeneğini kullanmayın. Bir tür kitaplığından içeri aktarılmış bir derlemeden bir tür kitaplığını dışarı aktaramazsınız. **/Tlb** seçeneğinin kullanılması, tür kitaplığı verme programı ([Tlbexp.exe](tlbexp-exe-type-library-exporter.md)) ve Regasm.exe ile aynı etkiye sahiptir ve bu, Tlbexp.exe oluşturduğu tür kitaplığını kaydetmediğinden emin olur.  Bir tür kitaplığını kaydetmek için **/tlb** seçeneğini kullanırsanız, tür kitaplığının kaydını silmek için **/tlb** seçeneğini **/Unregister** seçeneğiyle birlikte kullanabilirsiniz. İki seçeneği birlikte kullandığınızda tür kitaplığının ve arabirim girdilerinin kaydını kaldırırsınız, bu da kayıt defterini önemli ölçüde temizleyebilir.

Bir derlemeyi COM tarafından kullanılması için kaydettirdiğinize, Regasm.exe girdileri yerel bilgisayardaki kayıt defterine ekler. Daha ayrıntılı şekilde söylemek gerekirse, aynı derlemenin birden fazla sürümünün bir bilgisayarda yan yana çalışmasına olanak veren sürüme bağlı kayıt defteri anahtarları oluşturur. Bir derleme ilk kez kaydettirilirse, derleme için bir en üst düzey anahtar oluşturulur ve belirli bir sürüm için benzersiz bir alt anahtar oluşturulur. Derlemenin yeni bir sürümünü her kaydettirdiğinizde, Regasm.exe yeni sürüm için bir alt anahtar oluşturur.

Örneğin, COM tarafından kullanılmak üzere yönetilen bileşen myComp.dll'yi (sürüm 1.0.0.0) kaydettirdiğiniz bir senaryo düşünün. Daha sonra myComp.dll sürüm 2.0.0.0'ı kaydettiriyorsunuz. Bilgisayardaki tüm COM istemci uygulamalarının myComp.dll sürüm 2.0.0.0 kullandığını öğreniyor ve myComponent.dll sürüm 1.0.0.0'ın kaydını kaldırmaya karar veriyorsunuz. Bu kayıt defteri düzeni myComp.dll sürüm 1.0.0.0'ın kaydını kaldırmanıza olanak verir, çünkü yalnızca sürüm 1.0.0.0 alt anahtarı kaldırılmıştır.

Regasm.exe kullanarak bir derlemeyi kaydettikten sonra, herhangi bir COM istemcisinden etkinleştiribilmesini sağlamak için onu [genel bütünleştirilmiş kod önbelleğine](../app-domains/gac.md) yükleyebilirsiniz. Derleme yalnızca tek bir uygulamayla etkinleştirilecekse, onu söz konusu uygulamanın dizinine yerleştirebilirsiniz.

## <a name="examples"></a>Örnekler

Aşağıdaki komut içinde bulunan tüm ortak sınıfları kaydeder `myTest.dll` .

```console
regasm myTest.dll
```

Aşağıdaki komut `myTest.reg` , tüm gerekli kayıt defteri girdilerini içeren dosyayı oluşturur. Bu komut, kayıt defterini güncelleştirmez.

```console
regasm myTest.dll /regfile:myTest.reg
```

Aşağıdaki komut içinde bulunan tüm ortak sınıfları kaydeder `myTest.dll` ve `myTest.tlb` içinde tanımlanan tüm ortak türlerin tanımlarını içeren tür kitaplığını oluşturur ve kaydettirir `myTest.dll` .

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Tlbexp.exe (tür kitaplığı verme programı)](tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (tür kitaplığı Içeri Aktarıcı)](tlbimp-exe-type-library-importer.md)
- [Derlemeleri COM ile Kaydetme](../interop/registering-assemblies-with-com.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
