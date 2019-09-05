---
title: <useLegacyJit> Öğesi
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b783a82b1ef964de308532ef544bbfab2397400
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252219"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="f887e-102">\<useLegacyJit > öğesi</span><span class="sxs-lookup"><span data-stu-id="f887e-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="f887e-103">Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f887e-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="f887e-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f887e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f887e-105">&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="f887e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="f887e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit >**</span><span class="sxs-lookup"><span data-stu-id="f887e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f887e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f887e-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="f887e-108">Öğe adı `useLegacyJit` büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="f887e-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f887e-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="f887e-109">Attributes and elements</span></span>

<span data-ttu-id="f887e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f887e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f887e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f887e-111">Attributes</span></span>  
  
| <span data-ttu-id="f887e-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f887e-112">Attribute</span></span> | <span data-ttu-id="f887e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f887e-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="f887e-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f887e-114">Required attribute.</span></span><br><br><span data-ttu-id="f887e-115">Çalışma zamanının eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f887e-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="f887e-116">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="f887e-116">enabled attribute</span></span>  
  
| <span data-ttu-id="f887e-117">Değer</span><span class="sxs-lookup"><span data-stu-id="f887e-117">Value</span></span> | <span data-ttu-id="f887e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f887e-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="f887e-119">0</span><span class="sxs-lookup"><span data-stu-id="f887e-119">0</span></span>     | <span data-ttu-id="f887e-120">Ortak dil çalışma zamanı, .NET Framework 4,6 ve sonraki sürümlerde bulunan yeni 64-bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f887e-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="f887e-121">1\.</span><span class="sxs-lookup"><span data-stu-id="f887e-121">1</span></span>     | <span data-ttu-id="f887e-122">Ortak dil çalışma zamanı, eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f887e-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="f887e-123">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="f887e-123">Child elements</span></span>

<span data-ttu-id="f887e-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="f887e-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="f887e-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="f887e-125">Parent elements</span></span>  
  
| <span data-ttu-id="f887e-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="f887e-126">Element</span></span>         | <span data-ttu-id="f887e-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f887e-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="f887e-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f887e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="f887e-129">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="f887e-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="f887e-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f887e-130">Remarks</span></span>  

<span data-ttu-id="f887e-131">.NET Framework 4,6 ' den başlayarak, ortak dil çalışma zamanı, varsayılan olarak tam zamanında (JıT) derleme için yeni bir 64 bit derleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f887e-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="f887e-132">Bazı durumlarda bu durum, 64 bit JıT derleyicisi 'nin önceki sürümü tarafından derlenen uygulama kodundan kaynaklanan bir farklılık oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f887e-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="f887e-133">`enabled` Öğesinin özniteliğini olarak`1`ayarlayarak, yeni 64-bit JIT derleyicisini devre dışı bırakabilir ve bunun yerine eski 64 bit JIT derleyicisini kullanarak `<useLegacyJit>` uygulamanızı derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f887e-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f887e-134">`<useLegacyJit>` Öğesi yalnızca 64 bitlik JIT derlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="f887e-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="f887e-135">32 bit JıT derleyicisi ile derleme etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="f887e-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="f887e-136">Yapılandırma dosyası ayarı kullanmak yerine, eski 64 bit JıT derleyicisini iki farklı şekilde etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f887e-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="f887e-137">Ortam değişkenini ayarlama</span><span class="sxs-lookup"><span data-stu-id="f887e-137">Setting an environment variable</span></span>

  <span data-ttu-id="f887e-138">Ortam değişkenini ya `0` (yeni 64-bit JIT derleyicisini kullanın) veya `1` (eski 64 bit JIT derleyicisini kullanın) olarak ayarlayın: `COMPLUS_useLegacyJit`</span><span class="sxs-lookup"><span data-stu-id="f887e-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="f887e-139">Ortam değişkeni *genel kapsama*sahiptir, yani makinede çalıştırılan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f887e-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="f887e-140">Ayarlanırsa, uygulama yapılandırma dosyası ayarı tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="f887e-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="f887e-141">Ortam değişkeni adı büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f887e-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="f887e-142">Kayıt defteri anahtarı ekleme</span><span class="sxs-lookup"><span data-stu-id="f887e-142">Adding a registry key</span></span>

  <span data-ttu-id="f887e-143">Kayıt defterindeki `REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` veya anahtarınabirdeğerekleyerekeski64bitJITderleyicisinietkinleştirebilirsiniz.`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`</span><span class="sxs-lookup"><span data-stu-id="f887e-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="f887e-144">Değer olarak adlandırılır `useLegacyJit`.</span><span class="sxs-lookup"><span data-stu-id="f887e-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="f887e-145">Değer 0 ise, yeni derleyici kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f887e-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="f887e-146">Değer 1 ise, eski 64 bit JıT derleyicisi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f887e-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="f887e-147">Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f887e-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="f887e-148">Değeri `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, makinede çalışan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f887e-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="f887e-149">Değeri `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, geçerli kullanıcı tarafından çalıştırılan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="f887e-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="f887e-150">Bir makine birden çok kullanıcı hesabıyla yapılandırıldıysa, değer diğer kullanıcılar için de kayıt defteri anahtarlarına eklenmediği sürece yalnızca geçerli kullanıcı tarafından çalıştırılan uygulamalar etkilenir.</span><span class="sxs-lookup"><span data-stu-id="f887e-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="f887e-151">`<useLegacyJit>` Öğesini bir yapılandırma dosyasına eklemek, varsa kayıt defteri ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="f887e-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f887e-152">Örnek</span><span class="sxs-lookup"><span data-stu-id="f887e-152">Example</span></span>  

<span data-ttu-id="f887e-153">Aşağıdaki yapılandırma dosyası, derlemeyi yeni 64-bit JıT derleyicisi ile devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f887e-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f887e-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f887e-154">See also</span></span>

- [<span data-ttu-id="f887e-155">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="f887e-155">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="f887e-156">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="f887e-156">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="f887e-157">Mayı Yeni 64-bit JıT derleyicisi</span><span class="sxs-lookup"><span data-stu-id="f887e-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
