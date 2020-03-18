---
title: .NET Core bileşenlerinin COM'a teşhir edilmesi
description: Bu öğretici, .NET Core'dan bir sınıfı COM'a nasıl gösteriş yapacaklarını gösterir. Kayıt Defteri'ne Göre COM sunucusu ve yan yana bir sunucu bildirimi oluşturursunuz.
ms.date: 07/12/2019
helpviewer_keywords:
- exposing .NET Core components to COM
- interoperation with unmanaged code, exposing .NET Core components
- COM interop, exposing COM components
ms.assetid: 21271167-fe7f-46ba-a81f-a6812ea649d4
author: jkoritzinsky
ms.author: jekoritz
ms.openlocfilehash: 98d303c99693a8aadb23da509a700772db69c0e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146664"
---
# <a name="exposing-net-core-components-to-com"></a>.NET Core bileşenlerinin COM'a teşhir edilmesi

.NET Core'da,.NET nesnelerinizi COM'a teşhir etme işlemi .NET Framework ile karşılaştırıldığında önemli ölçüde kolaylaştırılmıştır. Aşağıdaki işlem, bir sınıfı COM'a nasıl maruz bırakacağınız konusunda size yol gösterecektir. Bu öğretici şunların nasıl yapıldığını gösterir:

- .NET Core'dan bir sınıfı COM'a gösterin.
- .NET Core kitaplığınızı oluşturmanın bir parçası olarak bir COM sunucusu oluşturun.
- Kayıt Defteri'ne Göre Com için yan yana bir sunucu bildirimi otomatik olarak oluşturun.

## <a name="prerequisites"></a>Önkoşullar

- [.NET Core 3.0 SDK'yı](https://dotnet.microsoft.com/download) veya daha yeni bir sürümü yükleyin.

## <a name="create-the-library"></a>Kitaplığı oluşturma

İlk adım kitaplık oluşturmaktır.

1. Yeni bir klasör oluşturun ve bu klasörde aşağıdaki komutu çalıştırın:

    ```dotnetcli
    dotnet new classlib
    ```

2. `Class1.cs` dosyasını açın.
3. Dosyanın üstüne ekleyin. `using System.Runtime.InteropServices;`
4. Adlı `IServer`bir arayüz oluşturun. Örnek:

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

5. Uyguladığınız `[Guid("<IID>")]` COM arabirimi için GUID arabirimi ile arabirime özniteliği ekleyin. Örneğin, `[Guid("fe103d6e-e71b-414c-80bf-982f18f6c1c7")]`. BU ARABIRIMIN COM için tek tanımlayıcısı olduğundan, bu GUID'nin benzersiz olması gerektiğini unutmayın. Visual Studio'da, GUID oluştur aracını açmak için Araçlar > GUID Oluştur'a giderek bir GUID oluşturabilirsiniz.
6. `[InterfaceType]` Arabirime özniteliği ekleyin ve arabiriminizin hangi temel COM arabirimlerini uygulaması gerektiğini belirtin.
7. 'yi uygulayan `Server` bir sınıf oluşturun. `IServer`
8. `[Guid("<CLSID>")]` Uygulamakta olduğunuz COM sınıfı için sınıf tanımlayıcısı GUID ile sınıfa özniteliği ekleyin. Örneğin, `[Guid("9f35b6f5-2c05-4e7f-93aa-ee087f6e7ab6")]`. Bu arabirimin COM'a tek tanımlayıcısı olduğundan, bu GUID arabiriminde olduğu gibi benzersiz olmalıdır.
9. `[ComVisible(true)]` Özniteliği hem arabirime hem de sınıfa ekleyin.

> [!IMPORTANT]
> .NET Framework'ün aksine,.NET Core, COM aracılığıyla etkinleştirilebilir olmasını istediğiniz herhangi bir sınıfın CLSID'sini belirtmenizi gerektirir.

## <a name="generate-the-com-host"></a>COM ana bilgisayarını oluşturma

1. Proje `.csproj` dosyasını açın `<EnableComHosting>true</EnableComHosting>` ve `<PropertyGroup></PropertyGroup>` etiketin içine ekleyin.
2. Projeyi derleyin.

Elde edilen çıktı , `ProjectName.dll` `ProjectName.deps.json`, `ProjectName.runtimeconfig.json` `ProjectName.comhost.dll` ve dosya olacaktır.

## <a name="register-the-com-host-for-com"></a>COM ana bilgisayarını COM için kaydedin

Yükseltilmiş bir komut istemini `regsvr32 ProjectName.comhost.dll`açın ve çalıştırın. Bu, tüm maruz kalan .NET nesnelerinizi COM'a kaydeder.

## <a name="enabling-regfree-com"></a>RegFree COM'u etkinleştirme

1. Proje `.csproj` dosyasını açın `<EnableRegFreeCom>true</EnableRegFreeCom>` ve `<PropertyGroup></PropertyGroup>` etiketin içine ekleyin.
2. Projeyi derleyin.

Elde edilen çıktı artık bir `ProjectName.X.manifest` dosyaya da sahip olacaktır. Bu dosya, Kayıt Defteri-Free COM ile kullanılmak üzere yan yana tezahürüdür.

## <a name="sample"></a>Örnek

GitHub'daki dotnet/numune deposunda tam işlevsel bir [COM sunucu örneği](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo) vardır.

## <a name="additional-notes"></a>Ek notlar

.NET Framework'ün aksine, .NET Core derlemesinden BIR COM Türü Kitaplığı (TLB) oluşturmak için .NET Core'da destek yoktur. Kılavuz, COM arabirimlerinin yerel bildirimleri için bir IDL dosyasını veya C/C++ üstbilgisini el ile yazmaktır.

Ayrıca, hem .NET Framework hem de .NET Core'un aynı işleme yüklenmesi tanılama sınırlamaları vardır. Hem .NET Framework hem de .NET Core'u aynı anda hata ayıklamak mümkün olmadığı için, birincil sınırlama yönetilen bileşenlerin hata ayıklanmasıdır. Buna ek olarak, iki çalışma zamanı örneği yönetilen derlemeleri paylaşmaz. Bu, gerçek .NET türlerini iki çalışma zamanında paylaşmanın mümkün olmadığı ve bunun yerine tüm etkileşimlerin açıklanmış COM arabirim sözleşmeleri ile sınırlandırılması gerektiği anlamına gelir.
