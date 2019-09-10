---
title: .NET Core Bileşenlerini COM’da Gösterme
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 686d1b31478121a8b2c907d99672a5fcc3438a71
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849036"
---
# <a name="exposing-net-core-components-to-com"></a>.NET Core Bileşenlerini COM’da Gösterme

.NET Core 'da, .NET nesnelerinizi COM 'a sunma süreci, .NET Framework karşılaştırmaya kıyasla önemli ölçüde basitleştirilmiştir. Aşağıdaki süreç, bir sınıfı COM 'a nasıl kullanıma sunabileceğiniz konusunda size yol gösterecektir. Bu öğreticide nasıl yapılacağı gösterilmektedir:

- .NET Core 'dan COM 'a bir sınıf sunun.
- .NET Core kitaplığınızı oluşturmanın bir parçası olarak bir COM sunucusu oluşturun.
- Kayıt defteri ücretsiz COM için otomatik olarak yan yana sunucu bildirimi oluşturun.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3,0 Preview 7 SDK 'sını](https://dotnet.microsoft.com/download) veya daha yeni bir sürümünü yükler.

## <a name="create-the-library"></a>Kitaplığı oluşturma

İlk adım, kitaplığı oluşturmaktır.

1. Yeni bir klasör oluşturun ve bu klasörde ' i çalıştırın `dotnet new classlib`.
2. Açık `Class1.cs`.
3. Dosyanın `using System.Runtime.InteropServices;` en üstüne ekleyin.
4. Adlı `IServer`bir arabirim oluşturun. Örneğin:[!code-csharp[The IServer interface](~/samples/core/extensions/COMServerDemo/COMContract/IServer.cs)]
5. `[Guid("<IID>")]` Öğesini, uygulamayı uyguladığınız com arabirimi için arabirim GUID 'i ile birlikte arabirimine ekleyin. Örneğin: `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Bu GUID 'nin COM için bu arabirimin tek tanımlayıcısı olduğundan, bu GUID 'in benzersiz olması gerektiğini unutmayın. Visual Studio 'da, GUID oluştur ' a giderek bir GUID oluşturabilirsiniz > Guid Oluştur aracını açın.
6. `[InterfaceType]` Arabirimine özniteliği ekleyin ve arabiriminizdeki hangi temel com arabirimlerini uygulanacağını belirtin.
7. `Server` Uygulayan`IServer`adlı bir sınıf oluşturun.
8. `[Guid("<CLSID>")]` Öğesini, uyguladığınız com sınıfı için sınıf tanımlayıcısı GUID 'i ile sınıfına ekleyin. Örneğin: `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Arabirim GUID 'SI ile olduğu gibi bu GUID, bu arabirimin COM için tek tanımlayıcısı olduğundan benzersiz olmalıdır.
9. `[ComVisible(true)]` Özniteliğini hem arabirimine hem de sınıfına ekleyin.

> [!IMPORTANT]
> .NET Framework aksine, .NET Core, COM üzerinden etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID 'sini belirtmenizi gerektirir.

## <a name="generate-the-com-host"></a>COM konağını oluşturma

1. Proje dosyasını açın ve `<PropertyGroup></PropertyGroup>` etiketinin içine `<EnableComHosting>true</EnableComHosting>` ekleyin. `.csproj`
2. Projeyi oluşturun.

`ProjectName.dll`Elde edilen çıktıda bir `ProjectName.deps.json` `ProjectName.runtimeconfig.json` , ve`ProjectName.comhost.dll` dosyası olacaktır.

## <a name="register-the-com-host-for-com"></a>Com için COM ana bilgisayarını kaydetme

Yükseltilmiş bir komut istemi açın ve çalıştırın `regsvr32 ProjectName.comhost.dll`. Bu, tüm sunulan .NET nesnelerinizi COM ile kaydeder.

## <a name="enabling-regfree-com"></a>RegFree COM etkinleştiriliyor

1. Proje dosyasını açın ve `<PropertyGroup></PropertyGroup>` etiketinin içine `<EnableRegFreeCom>true</EnableRegFreeCom>` ekleyin. `.csproj`
2. Projeyi oluşturun.

Sonuçta elde edilen çıkışın bir `ProjectName.X.manifest` dosyası da olacaktır. Bu dosya, kayıt defteri-ücretsiz COM ile kullanılmak üzere yan yana bildirimidir.

## <a name="sample"></a>Örnek

GitHub 'daki DotNet/Samples deposunda tam işlevli bir [com sunucusu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.

## <a name="additional-notes"></a>Ek notlar

.NET Framework aksine bir .NET Core derlemesinden COM tür kitaplığı (TLB) oluşturmaya yönelik .NET Core desteği yoktur. Arabirimlerinizin yerel bildirimleri için el ile bir IDL dosyası ya da C++ bir üst bilgi yazmanız gerekecektir.

Ayrıca, hem .NET Framework hem de .NET Core 'u aynı işleme yüklemek desteklenmez ve bir .NET Core COM sunucusunun bir .NET Framework COM istemci işlemine yüklenmesi veya tam tersi desteklenmez.
