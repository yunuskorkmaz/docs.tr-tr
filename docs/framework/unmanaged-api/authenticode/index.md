---
description: 'Daha fazla bilgi edinin: Authenticode (yönetilmeyen API Başvurusu)'
title: Authenticode (Yönetilmeyen API Başvurusu)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 0a4a9b4ba3cc9a5818896508c80bc31073f514e7
ms.sourcegitcommit: 26721a2260deabb3318cc98af8619306711153cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2021
ms.locfileid: "105027850"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (Yönetilmeyen API Başvurusu)

Authenticode XrML lisans oluşturma ve doğrulama modülünü destekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [_AxlGetIssuerPublicKeyHash İşlevi](axlgetissuerpublickeyhash-function.md)  
 Belirtilen sertifikayı imzalamak için kullanılan özel anahtarla ilişkili ortak anahtarın SHA-1 karmasını alır.  
  
 [_AxlPublicKeyBlobToPublicKeyToken İşlevi](axlpublickeyblobtopublickeytoken-function.md)  
 Bir CSP PUBLICKEYBLOB biçiminden tanımlayıcı ad ortak anahtar belirtecini hesaplar.  
  
 [_AxlRSAKeyValueToPublicKeyToken İşlevi](axlrsakeyvaluetopublickeytoken-function.md)  
 Bir mod ve üs değeri bir tanımlayıcı ad ortak anahtar belirtecine dönüştürür.  
  
 [CertFreeAuthenticodeSignerInfo İşlevi](certfreeauthenticodesignerinfo-function.md)  
 AXL_AUTHENTICODE_SIGNER_INFO yapısı için ayrılan kaynakları boşaltır.  
  
 [CertFreeAuthenticodeTimestamperInfo İşlevi](certfreeauthenticodetimestamperinfo-function.md)  
 AXL_AUTHENTICODE_TIMESTAMPER_INFO yapısı için ayrılan kaynakları boşaltır.  
  
 [CertTimestampAuthenticodeLicense İşlevi](certtimestampauthenticodelicense-function.md)  
 Zaman damgaları CertCreateAuthenticodeLicense tarafından oluşturulan bir Authenticode XrML lisansı.  
  
 [CertVerifyAuthenticodeLicense İşlevi](certverifyauthenticodelicense-function.md)  
 Authenticode XrML lisansının geçerliliğini doğrular.  
  
 [AXL_AUTHENTICODE_SIGNER_INFO Yapısı](axl-authenticode-signer-info-structure.md)  
 Authenticode imzalayan bilgilerini tanımlar.  
  
 [AXL_AUTHENTICODE_TIMESTAMPER_INFO Yapısı](axl-authenticode-timestamper-info-structure.md)  
 Authenticode zaman Stamper bilgilerini tanımlar.  

## <a name="requirements"></a>Gereksinimler

**Kitaplık**: clr.dll
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen API başvurusu](../index.md)
