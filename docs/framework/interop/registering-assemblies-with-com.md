---
title: Derlemeleri COM ile Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
ms.openlocfilehash: 9ff24a5705058d4e303b3b64b454ced8548053a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113800"
---
# <a name="registering-assemblies-with-com"></a>Derlemeleri COM ile Kaydetme
Bir derlemeyi COM ile kullanmak üzere kaydetmek veya kaydını silmek için [Derleme Kayıt Aracı (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) adlı bir komut satırı aracı çalıştırabilirsiniz. Regasm. exe, COM istemcilerinin .NET Framework sınıfını saydam bir şekilde kullanabilmesi için sistem kayıt defterine sınıf hakkında bilgi ekler. <xref:System.Runtime.InteropServices.RegistrationServices> Sınıfı eşdeğer işlevselliği sağlar.  
  
 Yönetilen bir bileşen, bir COM istemcisinden etkinleştirilmeden önce Windows kayıt defteri 'nde kayıtlı olmalıdır. Aşağıdaki tabloda, Regasm. exe ' nin tipik olarak Windows kayıt defterine eklediği anahtarlar gösterilmektedir. (000000 yazın, gerçek GUID değerini gösterir.)  
  
|GUID|Açıklama|Kayıt defteri anahtarı|  
|----------|-----------------|------------------|  
|IN|Sınıf tanımlayıcısı|HKEY_CLASSES_ROOT \CLSıD\\{000... 000|  
|'SI|Arabirim tanımlayıcısı|HKEY_CLASSES_ROOT \Interface\\{000... 000|  
|KITAPLıK KIMLIĞI|Kitaplık tanımlayıcısı|HKEY_CLASSES_ROOT \TypeLib\\{000... 000|  
|ProgID|Programlı tanımlayıcı|HKEY_CLASSES_ROOT 10.000... 000|  
  
 HKCR\CLSID\\{0000... 0000} anahtar, varsayılan değer sınıfının ProgID değerine ayarlanır ve iki yeni adlandırılmış değer, sınıf ve derleme eklenir. Çalışma zamanı, kayıt defterinden derleme değerini okur ve çalışma zamanı derleme çözümleyiciye geçirir. Derleme çözümleyici, ad ve sürüm numarası gibi derleme bilgilerine göre derlemeyi bulmaya çalışır. Bütünleştirilmiş kod Çözümleyicisinin bir derlemeyi bulması için, derlemenin aşağıdaki konumlardan birinde olması gerekir:  
  
- Genel bütünleştirilmiş kod önbelleği (tanımlayıcı adlandırılmış derleme olmalıdır).  
  
- , Uygulama dizininde. Uygulama yolundan yüklenen derlemelere yalnızca bu uygulamadan erişilebilir.  
  
- **/CODEBASE** seçeneğiyle birlikte bir dosya yolu ile regasm. exe olarak belirtilir.  
  
 Regasm. exe, HKCR\CLSID\\{0000... altında ınprocserver32 anahtarını da oluşturur. 0000} anahtar. Anahtar için varsayılan değer, ortak dil çalışma zamanını (mscoree. dll) başlatan DLL adına ayarlanır.  
  
## <a name="examining-registry-entries"></a>Kayıt Defteri Girdilerini İnceleme  
 COM birlikte çalışması, herhangi bir .NET Framework sınıfının bir örneğini oluşturmak için standart bir sınıf fabrikası uygulamasına sahiptir. İstemciler, bir sınıf fabrikası almak ve diğer tüm COM bileşenleri gibi nesneleri oluşturmak için yönetilen DLL üzerinde **DllGetClassObject** çağırabilir.  
  
 `InprocServer32` Alt anahtar için, ortak dil çalışma zamanının yönetilen nesneyi oluşturduğunu göstermek üzere, geleneksel bir com tür kitaplığı yerine Mscoree. dll başvurusu görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Nasıl yapılır: COM'dan .NET Türlerine Başvurma](how-to-reference-net-types-from-com.md)
- [.NET nesnesi çağırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [COM erişimi için uygulama dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
