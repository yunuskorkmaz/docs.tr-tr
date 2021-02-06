---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi'
title: 'ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: 3488cab9ee21ea027e16089f066369ab8c6c69d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659549"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a><span data-ttu-id="fcb55-103">ICorDebugSymbolProvider2:: Getgenericdictionaryınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcb55-103">ICorDebugSymbolProvider2::GetGenericDictionaryInfo Method</span></span>

<span data-ttu-id="fcb55-104">Genel sözlük eşlemesini alır.</span><span class="sxs-lookup"><span data-stu-id="fcb55-104">Retrieves a generic dictionary map.</span></span>

## <a name="syntax"></a><span data-ttu-id="fcb55-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcb55-105">Syntax</span></span>

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a><span data-ttu-id="fcb55-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcb55-106">Parameters</span></span>

`ppMemoryBuffer`\
<span data-ttu-id="fcb55-107">dışı Genel sözlük eşlemesini içeren bir [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fcb55-107">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object containing the generic dictionary map.</span></span> <span data-ttu-id="fcb55-108">Daha fazla bilgi için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fcb55-108">See the Remarks section for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcb55-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcb55-109">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="fcb55-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fcb55-110">This method is available with .NET Native only.</span></span>

<span data-ttu-id="fcb55-111">Eşleme iki üst düzey bölümden oluşur:</span><span class="sxs-lookup"><span data-stu-id="fcb55-111">The map consists of two top-level sections:</span></span>

- <span data-ttu-id="fcb55-112">Bu haritaya dahil olan tüm sözlüklerin göreli sanal adreslerini (RVA) içeren bir [Dizin](#Directory) .</span><span class="sxs-lookup"><span data-stu-id="fcb55-112">A [directory](#Directory) containing the relative virtual addresses (RVA) of all dictionaries included in this map.</span></span>

- <span data-ttu-id="fcb55-113">Nesne örneği oluşturma bilgilerini içeren bayt hizalanmış [yığın](#Heap) .</span><span class="sxs-lookup"><span data-stu-id="fcb55-113">A byte-aligned [heap](#Heap) that contains object instantiation information.</span></span> <span data-ttu-id="fcb55-114">Son dizin girdisinden hemen sonra başlar.</span><span class="sxs-lookup"><span data-stu-id="fcb55-114">It starts immediately after the last directory entry.</span></span>

<a name="Directory"></a>

## <a name="the-directory"></a><span data-ttu-id="fcb55-115">Dizin</span><span class="sxs-lookup"><span data-stu-id="fcb55-115">The Directory</span></span>

<span data-ttu-id="fcb55-116">Dizindeki her giriş, yığın içindeki bir uzaklığa başvurur; diğer bir deyişle, yığının başlangıcına göre bir uzaklıkdır.</span><span class="sxs-lookup"><span data-stu-id="fcb55-116">Each entry in the directory refers to an offset inside the heap; that is, it is an offset that is relative to the start of the heap.</span></span> <span data-ttu-id="fcb55-117">Tek tek girişlerin değeri benzersiz değildir; birden çok dizin girişinin yığında aynı sapmayı göstermesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="fcb55-117">The value of individual entries is not necessarily unique; it is possible for multiple directory entries to point to the same offset in the heap.</span></span>

<span data-ttu-id="fcb55-118">Genel sözlük eşlemesinin dizin bölümü aşağıdaki yapıya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="fcb55-118">The directory portion of the generic dictionary map has the following structure:</span></span>

- <span data-ttu-id="fcb55-119">İlk 4 bayt sözlük girişi sayısını (yani, Sözlükteki göreli sanal adreslerin sayısını) içerir.</span><span class="sxs-lookup"><span data-stu-id="fcb55-119">The first 4 bytes contains the number of dictionary entries (that is, the number of relative virtual addresses in the dictionary).</span></span> <span data-ttu-id="fcb55-120">Bu değere *N* olarak başvuracağız. Yüksek bit ayarlandıysa, girişler göreli sanal adrese göre artan sırada sıralanır.</span><span class="sxs-lookup"><span data-stu-id="fcb55-120">We will refer to this value as *N*. If the high bit is set, the entries are sorted by relative virtual address in ascending order.</span></span>

- <span data-ttu-id="fcb55-121">*N* Dizin girdileri izler.</span><span class="sxs-lookup"><span data-stu-id="fcb55-121">The *N* directory entries follow.</span></span> <span data-ttu-id="fcb55-122">Her giriş, 2 4 baytlık kesimlerde 8 bayttan oluşur:</span><span class="sxs-lookup"><span data-stu-id="fcb55-122">Each entry consists of 8 bytes, in two 4-byte segments:</span></span>

  - <span data-ttu-id="fcb55-123">Bayt 0-3: RVA; sözlüğün göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="fcb55-123">Bytes 0-3: RVA; the dictionary's relative virtual address.</span></span>

  - <span data-ttu-id="fcb55-124">Bayt 4-7: konum; yığının başlangıcına göre bir göreli konum.</span><span class="sxs-lookup"><span data-stu-id="fcb55-124">Bytes 4-7: Offset; an offset relative to the start of the heap.</span></span>

<a name="Heap"></a>

## <a name="the-heap"></a><span data-ttu-id="fcb55-125">Yığın</span><span class="sxs-lookup"><span data-stu-id="fcb55-125">The Heap</span></span>

<span data-ttu-id="fcb55-126">Yığın boyutu + 4 dizin boyutundan akışın uzunluğu çıkartılacak şekilde bir akış okuyucusu tarafından hesaplanabilir.</span><span class="sxs-lookup"><span data-stu-id="fcb55-126">The heap’s size can be computed by a stream reader by subtracting the length of the stream from the directory size + 4.</span></span> <span data-ttu-id="fcb55-127">Diğer bir deyişle:</span><span class="sxs-lookup"><span data-stu-id="fcb55-127">In other words:</span></span>

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

<span data-ttu-id="fcb55-128">Dizin boyutunun nerede olduğu `N * 8` .</span><span class="sxs-lookup"><span data-stu-id="fcb55-128">where the directory size is `N * 8`.</span></span>

<span data-ttu-id="fcb55-129">Yığındaki her bir örnek oluşturma bilgi öğesinin biçimi:</span><span class="sxs-lookup"><span data-stu-id="fcb55-129">The format for each instantiation information item on the heap is:</span></span>

- <span data-ttu-id="fcb55-130">Bu örnek oluşturma bilgi öğesinin sıkıştırılmış ECMA meta veri biçimindeki bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="fcb55-130">The length of this instantiation information item in bytes in compressed ECMA metadata format.</span></span> <span data-ttu-id="fcb55-131">Değer bu uzunluk bilgilerini dışlar.</span><span class="sxs-lookup"><span data-stu-id="fcb55-131">The value excludes this length information.</span></span>

- <span data-ttu-id="fcb55-132">Sıkıştırılmış ECMA meta veri biçimindeki genel örnek oluşturma türlerinin veya *T*'nin sayısı.</span><span class="sxs-lookup"><span data-stu-id="fcb55-132">The number of generic instantiation types, or *T*, in compressed ECMA metadata format.</span></span>

- <span data-ttu-id="fcb55-133">*T* türleri, her biri ECMA tür imza biçiminde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="fcb55-133">*T* types, each represented in ECMA type signature format.</span></span>

<span data-ttu-id="fcb55-134">Her yığın öğesinin uzunluğunun dahil edilmesi, yığın etkilenmeden dizin bölümünün basit sıralanmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="fcb55-134">The inclusion of the length for each heap element enables simple sorting of the directory section without affecting the heap.</span></span>

## <a name="requirements"></a><span data-ttu-id="fcb55-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcb55-135">Requirements</span></span>

<span data-ttu-id="fcb55-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcb55-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="fcb55-137">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fcb55-137">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="fcb55-138">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fcb55-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fcb55-139">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcb55-139">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fcb55-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcb55-140">See also</span></span>

- [<span data-ttu-id="fcb55-141">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fcb55-141">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="fcb55-142">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fcb55-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
