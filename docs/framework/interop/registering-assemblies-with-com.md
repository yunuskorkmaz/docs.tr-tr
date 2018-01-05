---
title: Derlemeleri COM ile Kaydetme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1473fa07b57dcd19ea192db6cdb0a395f119b159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="registering-assemblies-with-com"></a>Derlemeleri COM ile Kaydetme
Adlı bir komut satırı aracını çalıştırabilirsiniz [derleme Kayıt Aracı (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) kaydetmek veya com ile kullanmak için bir derleme kaydını kaldırma COM istemcileri .NET Framework sınıf şeffaf bir şekilde kullanabilmeniz için Regasm.exe Sistem kayıt defterine sınıfı hakkında bilgi ekler. <xref:System.Runtime.InteropServices.RegistrationServices> Sınıfı eşdeğer işlevsellik sağlar.  
  
 Bir COM istemciden etkinleştirilmeden önce yönetilen bileşenin Windows Kayıt Defteri'nde kaydedilmesi gerekir. Aşağıdaki tabloda Regasm.exe genellikle Windows kayıt defterine ekler anahtarlarını gösterir. (000000 gerçek GUID değeri gösterir.)  
  
|GUID|Açıklama|Kayıt defteri anahtarı|  
|----------|-----------------|------------------|  
|CLSID|Sınıf tanımlayıcısı|HKEY_CLASSES_ROOT\CLSID\\{000... 000}|  
|IID|Arabirim tanımlayıcısı|HKEY_CLASSES_ROOT\Interface\\{000... 000}|  
|KİTAPLIK KİMLİĞİ|Tür kitaplığı tanımlayıcısı|HKEY_CLASSES_ROOT\TypeLib\\{000... 000}|  
|ProgID|Program tanımlayıcısı|HKEY_CLASSES_ROOT\000... 000|  
  
 HKCR\CLSID altında\\{0000... 0000} anahtarı, varsayılan değer sınıfı ProgID için ayarlanır ve iki yeni adlandırılmış değerler, sınıf ve derlemeyi eklenir. Çalışma zamanı derlemesi değerini kayıt defterinden okur ve çalışma zamanı derlemesi çözümleyicisini açın geçirir. Derleme Çözümleyicisi ad ve sürüm numarası gibi derleme bilgilere dayalı derleme bulmayı dener. Derleme Çözümleyicisi bütünleştirilmiş bulmak derleme aşağıdaki konumlardan birinde olması gerekir:  
  
-   Genel Derleme Önbelleği (tanımlayıcı adlı bir derleme olmalıdır).  
  
-   Uygulama dizini. Uygulama yolu yüklenen derlemeler yalnızca bu uygulamadan erişilebilir.  
  
-   İle belirtilen bir dosya yolu boyunca **/ codebase** Regasm.exe seçeneği.  
  
 RegAsm.exe da HKCR\CLSID Inprocserver32 anahtarında oluşturur\\{0000... 0000} anahtarı. Anahtar için varsayılan değeri, ortak dil çalışma zamanı (Mscoree.dll) başlatır DLL adına ayarlanır.  
  
## <a name="examining-registry-entries"></a>Kayıt Defteri Girdilerini İnceleme  
 COM birlikte çalışma herhangi bir .NET Framework sınıf örneği oluşturmak için bir standart sınıf Fabrika uygulamasını sağlar. İstemcileri çağırabilir **DllGetClassObject** bir üreteci almak ve herhangi bir COM bileşeni ile gibi nesneleri oluşturmak için yönetilen DLL üzerinde.  
  
 İçin `InprocServer32` alt anahtarı Mscoree.dll başvuru ortak dil çalışma zamanı yönetilen nesnesi oluşturur belirtmek için geleneksel COM tür kitaplığı yerine görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Framework Bileşenlerini COM'da Gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Nasıl yapılır: COM'dan .NET Türlerine Başvurma](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
 [Bir .NET nesnesini çağırma](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [COM erişim için bir uygulama dağıtma](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
