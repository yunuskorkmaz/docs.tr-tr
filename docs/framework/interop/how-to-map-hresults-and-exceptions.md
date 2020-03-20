---
title: 'Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
ms.openlocfilehash: e186228d1dc9a42ddfe92428f7dfad29a5789095
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181400"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Nasıl yapılır: HRESULTs ve Özel Durumları Eşleme
COM yöntemleri, HRESULTs döndürerek hataları rapor; .NET yöntemleri özel durumlar atarak bunları rapor. Çalışma zamanı ikisi arasındaki geçişi işler. .NET Framework eşlemlerinde bir HRESULT'a her özel durum sınıfı.  
  
 Kullanıcı tanımlı özel durum sınıfları, HRESULT'in uygun olduğu her şeyi belirtebilir. Bu özel durum sınıfları, özel durum nesnesi üzerinde **HResult** alanı ayarlayarak oluşturulduğunda döndürülecek HRESULT dinamik olarak değiştirebilirsiniz. Özel durum la ilgili ek bilgiler, yönetilmeyen işlemde .NET nesnesi üzerinde uygulanan **IErrorInfo** arabirimi aracılığıyla istemciye sağlanır.  
  
 **System.Exception'ı**genişleten bir sınıf oluşturursanız, inşaat sırasında HRESULT alanını ayarlamanız gerekir. Aksi takdirde, taban sınıf HRESULT değerini atar. İstisnanın oluşturucusundaki değeri sağlayarak yeni özel durum sınıflarını varolan bir HRESULT'a eşleyebilirsiniz.  
  
 İş parçacığı üzerinde bir hediye `HRESULT` olan durumlarda çalışma `IErrorInfo` zamanının bazen bir şeyi yok sayacağını unutmayın.  Bu davranış, ve aynı `HRESULT` hatayı `IErrorInfo` temsil etmez durumlarda oluşabilir.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Yeni bir özel durum sınıfı oluşturmak ve bir HRESULT ile eşlemek için  
  
1. Adlı `NoAccessException` yeni bir özel durum sınıfı oluşturmak ve HRESULT `E_ACCESSDENIED`ile eşlemek için aşağıdaki kodu kullanın.  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 Hem yönetilen hem de yönetilmeyen kodu aynı anda kullanan bir programla (herhangi bir programlama dilinde) karşılaşabilirsiniz. Örneğin, aşağıdaki kod örneğindeki özel mareşal, belirli bir HRESULT değeriyle özel bir özel durum atmak için **Marshal.ThrowExceptionForHR(int HResult)** yöntemini kullanır. Yöntem HRESULT'ı arar ve uygun özel durum türünü oluşturur. Örneğin, aşağıdaki kod parçasındaki HRESULT **ArgumentException**oluşturur.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Aşağıdaki tablo, her HRESULT'ın .NET Framework'deki karşılaştırılabilir özel durum sınıfına tam eşlemi sağlar.  
  
|HRESULT|.NET özel durumu|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**Appdomainunloadedexception**|  
|**COR_E_APPLICATION**|**Applicationexception**|  
|**COR_E_ARGUMENT veya E_INVALIDARG**|**Argumentexception**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**Argumentoutofrangeexception**|  
|**COR_E_ARITHMETIC veya ERROR_ARITHMETIC_OVERFLOW**|**Arithmeticexception**|  
|**COR_E_ARRAYTYPEMISMATCH**|**Arraytypemismatchexception**|  
|**COR_E_BADIMAGEFORMAT veya ERROR_BAD_FORMAT**|**Badımageformatexception**|  
|**COR_E_COMEMULATE_ERROR**|**KOMEDİÖZEL DURUM**|  
|**COR_E_CONTEXTMARSHAL**|**Contextmarshalexception**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**Cryptographicexception**|  
|**COR_E_DIRECTORYNOTFOUND veya ERROR_PATH_NOT_FOUND**|**Directorynotfoundexception**|  
|**COR_E_DIVIDEBYZERO**|**Dividebyzeroexception**|  
|**COR_E_DUPLICATEWAITOBJECT**|**Duplicatewaitobjectexception**|  
|**COR_E_ENDOFSTREAM**|**Endofstreamexception**|  
|**COR_E_TYPELOAD**|**Entrypointnotfoundexception**|  
|**COR_E_EXCEPTION**|**Özel durum**|  
|**COR_E_EXECUTIONENGINE**|**Executionengineexception**|  
|**COR_E_FIELDACCESS**|**Fieldaccessexception**|  
|**COR_E_FILENOTFOUND veya ERROR_FILE_NOT_FOUND**|**Filenotfoundexception**|  
|**COR_E_FORMAT**|**Formatexception**|  
|**COR_E_INDEXOUTOFRANGE**|**ındexoutofrangeexception**|  
|**COR_E_INVALIDCAST veya E_NOINTERFACE**|**ınvalidcastexception**|  
|**COR_E_INVALIDCOMOBJECT**|**ınvalidcomobjectexception**|  
|**COR_E_INVALIDFILTERCRITERIA**|**ınvalidfiltercriteriaexception**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**ınvalidolevarianttypeexception**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**Cor_e_ıo**|**ıoexception**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**Methodaccessexception**|  
|**COR_E_MISSINGFIELD**|**Missingfieldexception**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**Missingmanifestresourceexception**|  
|**COR_E_MISSINGMEMBER**|**Missingmemberexception**|  
|**COR_E_MISSINGMETHOD**|**Missingmethodexception**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**Multicastnotsupportedexception**|  
|**COR_E_NOTFINITENUMBER**|**Notfinitenumberexception**|  
|**E_notımpl**|**Notımplementedexception**|  
|**COR_E_NOTSUPPORTED**|**Notsupportedexception**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**Nullreferenceexception**|  
|**COR_E_OUTOFMEMORY veya**<br /><br /> **E_outofmemory**|**Outofmemoryexception**|  
|**COR_E_OVERFLOW**|**Overflowexception**|  
|**COR_E_PATHTOOLONG veya ERROR_FILENAME_EXCED_RANGE**|**Pathtoolongexception**|  
|**COR_E_RANK**|**Rankexception**|  
|**COR_E_REFLECTIONTYPELOAD**|**Reflectiontypeloadexception**|  
|**COR_E_REMOTING**|**Remotingexception**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**Safearraytypemismatchexception**|  
|**COR_E_SECURITY**|**Securityexception**|  
|**COR_E_SERIALIZATION**|**Serializationexception**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**Stackoverflowexception**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**Synchronizationlockexception**|  
|**COR_E_SYSTEM**|**Systemexception**|  
|**COR_E_TARGET**|**Targetexception**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**Targetparametercountexception**|  
|**COR_E_THREADABORTED**|**Threadabortexception**|  
|**COR_E_THREADINTERRUPTED**|**Threadınterruptedexception**|  
|**COR_E_THREADSTATE**|**Threadstateexception**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**Typeloadexception**|  
|**COR_E_TYPEINITIALIZATION**|**Typeınitializationexception**|  
|**COR_E_VERIFICATION**|**Verificationexception**|  
|**COR_E_WEAKREFERENCE**|**Zayıf Referans Özel Durum**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Diğer tüm HRESULTs**|**Comexception**|  
  
 Genişletilmiş hata bilgilerini almak için yönetilen istemcinin oluşturulan özel durum nesnesinin alanlarını incelemesi gerekir. Özel durum nesnesinin bir hata hakkında yararlı bilgiler sağlaması için COM nesnesinin **IErrorInfo** arabirimini uygulaması gerekir. Çalışma süresi, özel durum nesnesini başlatmayı sağlamak için **IErrorInfo** tarafından sağlanan bilgileri kullanır.  
  
 COM nesnesi **IErrorInfo'yu**desteklemiyorsa, çalışma zamanı varsayılan değerlere sahip bir özel durum nesnesini başolarak laştırır. Aşağıdaki tablo, bir özel durum nesnesi ile ilişkili her alanı listeler ve COM nesnesi **IErrorInfo'yu**desteklediğinde varsayılan bilgilerin kaynağını tanımlar.  
  
 İş parçacığı üzerinde bir hediye `HRESULT` olan durumlarda çalışma `IErrorInfo` zamanının bazen bir şeyi yok sayacağını unutmayın.  Bu davranış, ve aynı `HRESULT` hatayı `IErrorInfo` temsil etmez durumlarda oluşabilir.  
  
|Özel durum alanı|COM'dan Bilgi Kaynağı|  
|---------------------|------------------------------------|  
|**Hata Kodu**|HRESULT çağrıdan döndü.|  
|**Helplink**|**IErrorInfo->HelpContext** sıfır değilse, dize **IErrorInfo->GetHelpFile** ve "#" ve **IErrorInfo->GetHelpContext**concatenating oluşur. Aksi takdirde dize **IErrorInfo->GetHelpFile**döndürülür.|  
|**ınnerexception**|Her zaman bir null referans (Visual Basic**hiçbir şey).**|  
|**İleti**|String **IErrorInfo->GetDescription**döndü.|  
|**Kaynak**|String **IErrorInfo->GetSource**döndü.|  
|**Stacktrace**|Yığın izi.|  
|**Hedef Sitesi**|Başarısız HRESULT döndürülen yöntemin adı.|  
  
 **İleti,** **Kaynak**ve **StackTrace** gibi özel durum alanları **StackOverflowException**için kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş COM Birlikte Çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Özel durumlar](../../standard/exceptions/index.md)
