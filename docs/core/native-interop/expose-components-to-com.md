---
title: .NET Core bileşenlerini COM 'a gösterme
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 301177113f67748b62ea2686615cfe5378fdc2fd
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157550"
---
# <a name="exposing-net-core-components-to-com"></a>.NET Core bileşenlerini COM 'a gösterme

.NET Core 'da, .NET nesnelerinizi COM 'a sunma süreci, .NET Framework karşılaştırmaya kıyasla önemli ölçüde basitleştirilmiştir. Aşağıdaki süreç, bir sınıfı COM 'a nasıl kullanıma sunabileceğiniz konusunda size yol gösterecektir. Bu öğretici şunların nasıl yapıldığını gösterir:

- .NET Core 'dan COM 'a bir sınıf sunun.
- .NET Core kitaplığınızı oluşturmanın bir parçası olarak bir COM sunucusu oluşturun.
- Kayıt defteri ücretsiz COM için otomatik olarak yan yana sunucu bildirimi oluşturun.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download) veya daha yeni bir sürümü yükler.

## <a name="create-the-library"></a>Kitaplığı oluşturma

İlk adım, kitaplığı oluşturmaktır.

1. Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet new classlib
    ```

2. `Class1.cs` programını açın.
3. `using System.Runtime.InteropServices;` dosyanın en üstüne ekleyin.
4. `IServer`adlı bir arabirim oluşturun. Örnek:

   [!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]

5. `[Guid("<IID>")]` özniteliğini, uyguladığınız COM arabirimi için arabirim GUID 'i ile ekleyin. Örneğin, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Bu GUID 'nin COM için bu arabirimin tek tanımlayıcısı olduğundan, bu GUID 'in benzersiz olması gerektiğini unutmayın. Visual Studio 'da, GUID oluştur ' a giderek bir GUID oluşturabilirsiniz > Guid Oluştur aracını açın.
6. Arabirimine `[InterfaceType]` özniteliğini ekleyin ve arayüzün hangi temel COM arabirimlerini uygulanacağını belirtin.
7. `IServer`uygulayan `Server` adlı bir sınıf oluşturun.
8. Uyguladığınız COM sınıfı için sınıf tanımlayıcı GUID 'i ile sınıfa `[Guid("<CLSID>")]` özniteliğini ekleyin. Örneğin, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Arabirim GUID 'SI ile olduğu gibi bu GUID, bu arabirimin COM için tek tanımlayıcısı olduğundan benzersiz olmalıdır.
9. `[ComVisible(true)]` özniteliğini hem arabirimine hem de sınıfına ekleyin.

> [!IMPORTANT]
> .NET Framework aksine, .NET Core, COM üzerinden etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID 'sini belirtmenizi gerektirir.

## <a name="generate-the-com-host"></a>COM konağını oluşturma

1. `.csproj` proje dosyasını açın ve bir `<PropertyGroup></PropertyGroup>` etiketinin içine `<EnableComHosting>true</EnableComHosting>` ekleyin.
2. Projeyi derleyin.

Sonuç çıktısı bir `ProjectName.dll`, `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` ve `ProjectName.comhost.dll` dosyasına sahip olur.

## <a name="register-the-com-host-for-com"></a>Com için COM ana bilgisayarını kaydetme

Yükseltilmiş bir komut istemi açın ve `regsvr32 ProjectName.comhost.dll`çalıştırın. Bu, tüm sunulan .NET nesnelerinizi COM ile kaydeder.

## <a name="enabling-regfree-com"></a>RegFree COM etkinleştiriliyor

1. `.csproj` proje dosyasını açın ve bir `<PropertyGroup></PropertyGroup>` etiketinin içine `<EnableRegFreeCom>true</EnableRegFreeCom>` ekleyin.
2. Projeyi derleyin.

Elde edilen çıkışın artık `ProjectName.X.manifest` bir dosyası da olacaktır. Bu dosya, kayıt defteri-ücretsiz COM ile kullanılmak üzere yan yana bildirimidir.

## <a name="sample"></a>Örnek

GitHub 'daki DotNet/Samples deposunda tam işlevli bir [com sunucusu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.

## <a name="additional-notes"></a>Ek notlar

.NET Framework aksine bir .NET Core derlemesinden COM tür kitaplığı (TLB) oluşturmaya yönelik .NET Core desteği yoktur. Bu kılavuz, COM arabirimlerinin yerel bildirimleri için el ile bir IDL dosyası yaC++ da bir C/üst bilgisi yazmaktır.

Ayrıca, hem .NET Framework hem de .NET Core 'u aynı işleme yüklemek için tanılama sınırlamaları vardır. Aynı anda hem .NET Framework hem de .NET Core hata ayıklaması mümkün olmadığından, birincil sınırlama yönetilen bileşenlerin hata ayıklaması olur. Ayrıca, iki çalışma zamanı örneği yönetilen derlemeleri paylaşmaz. Diğer bir deyişle, gerçek .NET türlerini iki çalışma sırasında paylaşmak mümkün değildir ve bunun yerine tüm etkileşimler sunulan COM arabirimi sözleşmeleri ile sınırlandırılmalıdır.
