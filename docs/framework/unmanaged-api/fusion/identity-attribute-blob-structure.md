---
title: IDENTITY_ATTRIBUTE_BLOB Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4c832a4bbc915749aadf435b204e084828698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434352"
---
# <a name="identityattributeblob-structure"></a>IDENTITY_ATTRIBUTE_BLOB Yapısı
Tek bir özniteliği derlemedeki hakkında bilgi içerir ve üç oluşur `DWORD`s. Her `DWORD` tarafından üretilen karakter arabellek içine bir uzaklık `CurrentIntoBuffer` yöntemi [Ienumıdentıty_attrıbute](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) arabirimi  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ofsNamespace`|Karakter arabellek içine ilk uzaklığı. Bu uzaklık özniteliğin ad alanı, ancak bir null karakter dizisi tarafından izlenmeyen. Bu nedenle, bu kullanılmaz.|  
|`ofsName`|Karakter arabellek içine ikinci uzaklığı. Bu konum özniteliğin adı başlangıcını işaretler.|  
|`ofsValue`|Karakter arabellek içine üçüncü uzaklığı. Bu konum özniteliğin değeri başlangıcını işaretler.|  
  
## <a name="sample"></a>Örnek  
 Aşağıdaki örnekte, sonuçta bir doldurulan neden birkaç temel adımlar gösterilmektedir `IDENTITY_ATTRIBUTE_BLOB` yapısı:  
  
1.  Elde bir [Ireferenceıdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) derleme için.  
  
2.  Çağrı `IReferenceIdentity::EnumAttributes` yöntemi ve elde bir [Ienumıdentıty_attrıbute](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md).  
  
3.  Bir karakter arabellek oluşturun ve olarak cast bir `IDENTITY_ATTRIBUTE_BLOB` yapısı.  
  
4.  Çağrı `CurrentIntoBuffer` yöntemi `IEnumIDENTITY_ATTRIBUTE` arabirimi. Bu yöntem öznitelikleri kopyalar `Namespace`, `Name`, ve `Value` karakter arabellek içine. Bu dizeler için üç uzaklıkları içinde kullanılabilir olacağı `IDENTITY_ATTRIBUTE_BLOB` yapısı.  
  
```  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||   
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity   
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;     
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],   
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",   
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),   
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =   
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed   
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =   
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
 C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll  
  
### <a name="sample-output"></a>Örnek çıktı  
 Culture = neutral =  
  
 adı Sistem =  
  
 processorArchitecture = MSIL  
  
 PublicKeyToken = b77a5c561934e089  
  
 Sürüm 2.0.0.0 =  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IReferenceIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 [IEnumIDENTITY_ATTRIBUTE Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 [IDENTITY_ATTRIBUTE Yapısı](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-structure.md)  
 [Fusion Yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
