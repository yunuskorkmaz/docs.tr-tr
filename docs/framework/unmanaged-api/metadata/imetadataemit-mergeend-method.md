---
description: ': Imetadatayayma:: MergeEnd yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::MergeEnd Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: aac48b9bafb60cee4e3d73232d9f9c00cca7f796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745885"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd Yöntemi

[Imetadatayayma:: Merge](imetadataemit-merge-method.md)için bir veya daha fazla önceki çağrı tarafından belirtilen tüm meta veri kapsamlarını geçerli kapsama birleştirir.

## <a name="syntax"></a>Sözdizimi

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>Parametreler

Bu yöntem hiçbir parametre alır.

## <a name="remarks"></a>Açıklamalar

Bu yordam, önceki çağrıları tarafından belirtilen tüm içeri aktarma kapsamlarından geçerli çıkış kapsamına gerçek meta verilerin birleştirilmesini tetikler `IMetaDataEmit::Merge` .

Aşağıdaki özel koşullar birleştirme için geçerlidir:

- İçeri aktarma kapsamındaki meta veriler için benzersiz olduğundan, bir modül sürümü tanımlayıcısı (MVıD) hiçbir şekilde içeri aktarılmaz.

- Modül genelinde mevcut özelliklerin üzerine yazılmaz.

  Geçerli kapsam için modül özellikleri zaten ayarlandıysa, hiçbir modül özelliği içeri aktarılmaz. Ancak, geçerli kapsamda modül özellikleri ayarlanmamışsa, ilk kez karşılaşıldığında yalnızca bir kez içeri aktarılır. Bu modül özelliklerine yeniden karşılaşılırsa, bunlar yinelemelerdir. Tüm modül özelliklerinin (MVıD hariç) değerleri karşılaştırılaysa ve yinelenen öğeler bulunmazsa bir hata oluşur.

- Tür tanımları ( `TypeDef` ) için, geçerli kapsamda birleştirilmemiş bir yineleme yok. `TypeDef`nesneler, *tam nitelikli nesne adı*  +  *GUID*  +  *sürüm numarasına* göre yinelemeler için denetlenir. Ad veya GUID üzerinde bir eşleşme varsa ve diğer iki öğe farklıysa, bir hata oluşur. Aksi takdirde, üç öğe de eşleşiyorsa, `MergeEnd` girişlerin gerçekten yinelendiğinden emin olmak için bir Amna hatlarıyla denetimi yapar; değilse bir hata oluşur. Bu Amna hatlarıyla denetimi şuna bakar:

  - Aynı sırada oluşan aynı üye bildirimleri. İşaretlenen Üyeler `mdPrivateScope` (bkz. [Cormethodadttr](cormethodattr-enumeration.md) sabit listesi) Bu denetim kapsamında değildir; özel olarak birleştirilir.

  - Aynı sınıf düzeni.

  Bu `TypeDef` , bir nesnenin, bildirildiği her meta veri kapsamında her zaman tam ve tutarlı bir şekilde tanımlanması gerektiği anlamına gelir; üye uygulamaları (bir sınıf için) birden çok derleme birimine yayılıyorsa, tam tanımın her kapsamda mevcut olduğu kabul edilir ve her kapsam için artımlı değildir. Örneğin, parametre adları sözleşmeyle ilgiliyse, her kapsama aynı şekilde yayılmaları gerekir; Bunlar ilgili değilse meta verilere yayılmamalıdır.

  Özel durum, bir `TypeDef` nesne, işaretlenmiş artımlı üyelere sahip olabilir `mdPrivateScope` . `MergeEnd`Bunlarla karşılaşmadan, yinelenenleri, yinelemeleri dikkate almadan geçerli kapsama ekler. Derleyici özel kapsamı anladığından, derleyicinin kuralları zorlarken sorumlu olması gerekir.

- Göreli sanal adresler (RVA) içeri aktarılmaz veya birleştirilmez; Derleyicinin bu bilgileri yeniden yayma beklenmektedir.

- Özel öznitelikler yalnızca, eklendiği öğe birleştirildiğinde birleştirilir. Örneğin, bir sınıfla ilişkili özel öznitelikler, sınıf ilk kez karşılaşıldığında birleştirilir. Özel öznitelikler, `TypeDef` derleme birimine özgü olan bir veya ile ilişkilendirilmişse `MemberDef` (bir üyenin derlenmesi zaman damgası gibi), birleştirilmez ve bu meta verileri kaldırmak veya güncelleştirmek için derleyiciye kadar olur.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** Cor. h

**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır

**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataEmit Arabirimi](imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](imetadataemit2-interface.md)
