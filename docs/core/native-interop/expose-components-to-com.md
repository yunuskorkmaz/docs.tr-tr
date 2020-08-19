---
title: .NET Core bileşenlerini COM 'a gösterme
description: Bu öğreticide, .NET Core 'dan bir sınıfın COM 'a nasıl sunulebileceği gösterilmektedir. Kayıt defteri-ücretsiz COM için bir COM sunucusu ve yan yana sunucu bildirimi oluşturabilirsiniz.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 346776ebae3a6077fd39f26d5bd19d599d163db2
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608339"
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

2. `Class1.cs` dosyasını açın.
3. `using System.Runtime.InteropServices;`Dosyanın en üstüne ekleyin.
4. Adlı bir arabirim oluşturun `IServer` . Örneğin:

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   [ComVisible(true)]
   [Guid(ContractGuids.ServerInterface)]
   [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
   public interface IServer
   {
       /// <summary>
       /// Compute the value of the constant Pi.
       /// </summary>
       double ComputePi();
   }
   ```

5. `[Guid("<IID>")]`Öğesini, uygulamayı UYGULADıĞıNıZ com arabirimi için ARABIRIM GUID 'i ile birlikte arabirimine ekleyin. Örneğin, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. Bu GUID 'nin COM için bu arabirimin tek tanımlayıcısı olduğundan, bu GUID 'in benzersiz olması gerektiğini unutmayın. Visual Studio 'da, GUID oluştur ' a giderek bir GUID oluşturabilirsiniz > Guid Oluştur aracını açın.
6. `[InterfaceType]`Arabirimine özniteliği ekleyin ve arabiriminizdeki hangi temel com arabirimlerini uygulanacağını belirtin.
7. Uygulayan adlı bir sınıf oluşturun `Server` `IServer` .
8. `[Guid("<CLSID>")]`Öğesini, UYGULADıĞıNıZ com sınıfı için sınıf tanımlayıcısı GUID 'i ile sınıfına ekleyin. Örneğin, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Arabirim GUID 'SI ile olduğu gibi bu GUID, bu arabirimin COM için tek tanımlayıcısı olduğundan benzersiz olmalıdır.
9. `[ComVisible(true)]`Özniteliğini hem arabirimine hem de sınıfına ekleyin.

> [!IMPORTANT]
> .NET Framework aksine, .NET Core, COM üzerinden etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID 'sini belirtmenizi gerektirir.

## <a name="generate-the-com-host"></a>COM konağını oluşturma

1. `.csproj`Proje dosyasını açın ve `<EnableComHosting>true</EnableComHosting>` etiketinin içine ekleyin `<PropertyGroup></PropertyGroup>` .
2. Projeyi derleyin.

Elde edilen çıktıda bir `ProjectName.dll` , `ProjectName.deps.json` `ProjectName.runtimeconfig.json` ve `ProjectName.comhost.dll` dosyası olacaktır.

## <a name="register-the-com-host-for-com"></a>Com için COM ana bilgisayarını kaydetme

Yükseltilmiş bir komut istemi açın ve çalıştırın `regsvr32 ProjectName.comhost.dll` . Bu, tüm sunulan .NET nesnelerinizi COM ile kaydeder.

## <a name="enabling-regfree-com"></a>RegFree COM etkinleştiriliyor

1. `.csproj`Proje dosyasını açın ve `<EnableRegFreeCom>true</EnableRegFreeCom>` etiketinin içine ekleyin `<PropertyGroup></PropertyGroup>` .
2. Projeyi derleyin.

Sonuçta elde edilen çıkışın bir dosyası da olacaktır `ProjectName.X.manifest` . Bu dosya, kayıt defteri-ücretsiz COM ile kullanılmak üzere yan yana bildirimidir.

## <a name="sample"></a>Örnek

GitHub 'daki DotNet/Samples deposunda tam işlevli bir [com sunucusu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.

## <a name="additional-notes"></a>Ek notlar

.NET Framework aksine bir .NET Core derlemesinden COM tür kitaplığı (TLB) oluşturmaya yönelik .NET Core desteği yoktur. Bu kılavuz, COM arabirimlerinin yerel bildirimleri için el ile bir IDL dosyası ya da C/C++ üst bilgisi yazmaktır.

COM bileşenlerinin [kendi kendine kapsanan dağıtımları](../deploying/index.md#publish-self-contained) desteklenmez. Yalnızca [çerçeveye BAĞıMLı](../deploying/index.md#publish-framework-dependent) com bileşenleri dağıtımları desteklenir.

Ayrıca, hem .NET Framework hem de .NET Core 'u aynı işleme yüklemek için tanılama sınırlamaları vardır. Aynı anda hem .NET Framework hem de .NET Core hata ayıklaması mümkün olmadığından, birincil sınırlama yönetilen bileşenlerin hata ayıklaması olur. Ayrıca, iki çalışma zamanı örneği yönetilen derlemeleri paylaşmaz. Diğer bir deyişle, gerçek .NET türlerini iki çalışma sırasında paylaşmak mümkün değildir ve bunun yerine tüm etkileşimler sunulan COM arabirimi sözleşmeleri ile sınırlandırılmalıdır.
