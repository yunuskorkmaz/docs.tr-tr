---
title: Derlemeleri COM ile Kaydetme
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3ba8cb41244157b1fca0f7e9d345625cc579d0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494047"
---
# <a name="registering-assemblies-with-com"></a>Derlemeleri COM ile Kaydetme
Adlı bir komut satırı aracını çalıştırdığınız [derleme Kayıt Aracı (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) kaydetmek veya com ile kullanmak için derleme kaydını kaldırmak için .NET Framework sınıfı COM istemcilerinin şeffaf bir şekilde kullanabilmeniz için RegAsm.exe'yi sınıfına ilişkin bilgileri sistem kayıt defterine ekler. <xref:System.Runtime.InteropServices.RegistrationServices> Sınıfı eşdeğer bir işlevselliği sağlar.  
  
 Bir COM istemciden etkinleştirilmeden önce bir yönetilen bileşen Windows kayıt defterine kaydedilmelidir. Aşağıdaki tablo, Regasm.exe genellikle Windows kayıt defterine ekler anahtarları gösterir. (000000 gerçek GUID değeri gösterir.)  
  
|GUID|Açıklama|Kayıt defteri anahtarı|  
|----------|-----------------|------------------|  
|CLSID|Sınıf tanımlayıcısı|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Arabirim tanımlayıcı|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|KİTAPLIK KİMLİĞİ|Tür kitaplığı tanımlayıcısı|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|Program Kimliği|Programlı tanımlayıcısı|HKEY_CLASSES_ROOT\000…000|  
  
 HKCR\CLSID altında\\{0000... 0000} anahtarı, varsayılan değer sınıfının ProgID için ayarlanır ve iki yeni adlandırılmış değerler, sınıf ve bütünleştirilmiş koduna eklenir. Çalışma zamanı derleme değeri Kayıt Defteri'nden okur ve çalışma zamanı derlemenin çözümleyici açın geçirir. Derleme Çözücü, ad ve sürüm numarası gibi derleme bilgileri temel alarak, derleme bulmayı dener. Derleme Çözücü bir derlemeyi bulmak derlemeyi aşağıdaki konumlardan birinde olmak zorundadır:  
  
-   Genel Derleme Önbelleği (tanımlayıcı adlı bütünleştirilmiş kod olmalıdır).  
  
-   Uygulama dizininde. Uygulama yolu yüklenen derlemeler, yalnızca bu uygulamadan erişilebilir.  
  
-   Belirtilen bir dosya yolu boyunca **/ codebase** Regasm.exe seçeneği.  
  
 RegAsm.exe da HKCR\CLSID Inprocserver32 anahtarında oluşturur\\{0000... 0000} anahtarı. Anahtar için varsayılan değer, ortak dil çalışma zamanı (Mscoree.dll) başlatır dll adına ayarlanır.  
  
## <a name="examining-registry-entries"></a>Kayıt Defteri Girdilerini İnceleme  
 COM birlikte çalışma, herhangi bir .NET Framework sınıfı örneğini oluşturmak için bir standart sınıf üreteci uygulamasını sağlar. İstemciler çağırabilir **DllGetClassObject** bir sınıf üreteci almak ve herhangi bir COM bileşeni ile olduğu gibi nesneleri oluşturmak için yönetilen DLL üzerinde.  
  
 İçin `InprocServer32` alt anahtarı Mscoree.dll başvuru, ortak dil çalışma zamanı Yönetilen Nesne oluşturduğunu göstermek için geleneksel COM tür kitaplığı yerine görüntülenir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [.NET Framework Bileşenlerini COM'da Gösterme](exposing-dotnet-components-to-com.md)
- [Nasıl yapılır: COM başvurusu .NET türlerinden](how-to-reference-net-types-from-com.md)
- [Bir .NET nesnesini çağırma](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))
- [COM erişimi için bir uygulama dağıtma](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
