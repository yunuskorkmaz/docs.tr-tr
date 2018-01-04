---
title: "ISymUnmanagedWriter::Initialize2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 015c7d43a856990251b3e67febe685759cc4e5fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a>ISymUnmanagedWriter::Initialize2 Yöntemi
İle bu yazıcısı ilişkili olacağı meta verileri verici arabirimi ayarlar ve hata ayıklama simgeleri yazılacak çıktı dosyası adını ayarlar. Bu yöntem, ayrıca program veritabanı (PDB) dosyasının son konumunu ayarlamanıza olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `emitter`  
 [in] Meta veri verici arayüzü için bir işaretçi.  
  
 `tempfilename`  
 [in] Bir işaretçi bir `WCHAR` hata ayıklama simgeleri yazılır dosya adını içerir. Dosya adları kullanmayan bir yazıcı için bir dosya adı belirtilirse, bu parametre yoksayılır.  
  
 `pIStream`  
 [in] Belirtilmişse, simge yazan simgeleri yayar verilen <xref:System.Runtime.InteropServices.ComTypes.IStream> yerine belirtilen dosyaya `filename` parametresi. `pIStream` Parametresi isteğe bağlıdır.  
  
 `fFullBuild`  
 [in] `true` bu tam bir yeniden oluşturma; ise `false` bu artımlı bir derleme ise.  
  
 `finalfilename`  
 [in] Bir işaretçi bir `WCHAR` diğer bir deyişle PDB dosyasının son konumu yol dizesini.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ISymUnmanagedWriter Arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [Initialize Yöntemi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
