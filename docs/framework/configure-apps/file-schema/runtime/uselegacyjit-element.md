---
title: <useLegacyJit> Öğesi
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
ms.openlocfilehash: a126b8c0050a8d1fd96a3d090f9b018a9faa07a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968850"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="6eb76-102">\<useLegacyJit> Öğesi</span><span class="sxs-lookup"><span data-stu-id="6eb76-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="6eb76-103">Ortak dil çalışma zamanının, Just-In-Time derlemesi için eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="6eb76-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<useLegacyJit>**  
  
## <a name="syntax"></a><span data-ttu-id="6eb76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6eb76-104">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="6eb76-105">Öğe adı `useLegacyJit` büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-105">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6eb76-106">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6eb76-106">Attributes and elements</span></span>

<span data-ttu-id="6eb76-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6eb76-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6eb76-108">Attributes</span></span>  
  
| <span data-ttu-id="6eb76-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6eb76-109">Attribute</span></span> | <span data-ttu-id="6eb76-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eb76-110">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="6eb76-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6eb76-111">Required attribute.</span></span><br><br><span data-ttu-id="6eb76-112">Çalışma zamanının eski 64-bit JıT derleyicisini kullanıp kullanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-112">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="6eb76-113">enabled özniteliği</span><span class="sxs-lookup"><span data-stu-id="6eb76-113">enabled attribute</span></span>  
  
| <span data-ttu-id="6eb76-114">Değer</span><span class="sxs-lookup"><span data-stu-id="6eb76-114">Value</span></span> | <span data-ttu-id="6eb76-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eb76-115">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="6eb76-116">0</span><span class="sxs-lookup"><span data-stu-id="6eb76-116">0</span></span>     | <span data-ttu-id="6eb76-117">Ortak dil çalışma zamanı, .NET Framework 4,6 ve sonraki sürümlerde bulunan yeni 64-bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-117">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="6eb76-118">1</span><span class="sxs-lookup"><span data-stu-id="6eb76-118">1</span></span>     | <span data-ttu-id="6eb76-119">Ortak dil çalışma zamanı, eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-119">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="6eb76-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6eb76-120">Child elements</span></span>

<span data-ttu-id="6eb76-121">Yok</span><span class="sxs-lookup"><span data-stu-id="6eb76-121">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="6eb76-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6eb76-122">Parent elements</span></span>  
  
| <span data-ttu-id="6eb76-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="6eb76-123">Element</span></span>         | <span data-ttu-id="6eb76-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6eb76-124">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="6eb76-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6eb76-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="6eb76-126">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-126">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="6eb76-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6eb76-127">Remarks</span></span>  

<span data-ttu-id="6eb76-128">.NET Framework 4,6 ' den başlayarak, ortak dil çalışma zamanı, varsayılan olarak tam zamanında (JıT) derleme için yeni bir 64 bit derleyicisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-128">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="6eb76-129">Bazı durumlarda bu durum, 64 bit JıT derleyicisi 'nin önceki sürümü tarafından derlenen uygulama kodundan kaynaklanan bir farklılık oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-129">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="6eb76-130">`enabled` `<useLegacyJit>` Öğesinin özniteliğini olarak ayarlayarak `1` , yeni 64-bit JIT derleyicisini devre dışı bırakabilir ve bunun yerine eskı 64 bit JIT derleyicisini kullanarak uygulamanızı derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6eb76-130">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6eb76-131">`<useLegacyJit>`Öğesi yalnızca 64 BITLIK JIT derlemesini etkiler.</span><span class="sxs-lookup"><span data-stu-id="6eb76-131">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="6eb76-132">32 bit JıT derleyicisi ile derleme etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-132">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="6eb76-133">Yapılandırma dosyası ayarı kullanmak yerine, eski 64 bit JıT derleyicisini iki farklı şekilde etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6eb76-133">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="6eb76-134">Ortam değişkenini ayarlama</span><span class="sxs-lookup"><span data-stu-id="6eb76-134">Setting an environment variable</span></span>

  <span data-ttu-id="6eb76-135">`COMPLUS_useLegacyJit`Ortam değişkenini ya `0` (yeni 64-bit JIT derleyicisini kullanın) veya `1` (eskı 64 bit JIT derleyicisini kullanın) olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="6eb76-135">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```env  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="6eb76-136">Ortam değişkeni *genel kapsama*sahiptir, yani makinede çalıştırılan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6eb76-136">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="6eb76-137">Ayarlanırsa, uygulama yapılandırma dosyası ayarı tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-137">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="6eb76-138">Ortam değişkeni adı büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-138">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="6eb76-139">Kayıt defteri anahtarı ekleme</span><span class="sxs-lookup"><span data-stu-id="6eb76-139">Adding a registry key</span></span>

  <span data-ttu-id="6eb76-140">`REG_DWORD` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` Kayıt defterindeki veya anahtarına bir değer ekleyerek eski 64 bit JIT derleyicisini etkinleştirebilirsiniz `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` .</span><span class="sxs-lookup"><span data-stu-id="6eb76-140">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="6eb76-141">Değer olarak adlandırılır `useLegacyJit` .</span><span class="sxs-lookup"><span data-stu-id="6eb76-141">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="6eb76-142">Değer 0 ise, yeni derleyici kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-142">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="6eb76-143">Değer 1 ise, eski 64 bit JıT derleyicisi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-143">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="6eb76-144">Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-144">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="6eb76-145">Değeri `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, makinede çalışan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6eb76-145">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="6eb76-146">Değeri `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` anahtara eklemek, geçerli kullanıcı tarafından çalıştırılan tüm uygulamaları etkiler.</span><span class="sxs-lookup"><span data-stu-id="6eb76-146">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="6eb76-147">Bir makine birden çok kullanıcı hesabıyla yapılandırıldıysa, değer diğer kullanıcılar için de kayıt defteri anahtarlarına eklenmediği sürece yalnızca geçerli kullanıcı tarafından çalıştırılan uygulamalar etkilenir.</span><span class="sxs-lookup"><span data-stu-id="6eb76-147">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="6eb76-148">`<useLegacyJit>`Öğesini bir yapılandırma dosyasına eklemek, varsa kayıt defteri ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6eb76-148">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eb76-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="6eb76-149">Example</span></span>  

<span data-ttu-id="6eb76-150">Aşağıdaki yapılandırma dosyası, derlemeyi yeni 64-bit JıT derleyicisi ile devre dışı bırakır ve bunun yerine eski 64 bit JıT derleyicisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6eb76-150">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6eb76-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6eb76-151">See also</span></span>

- [<span data-ttu-id="6eb76-152">\<runtime>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6eb76-152">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="6eb76-153">\<configuration>Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="6eb76-153">\<configuration> Element</span></span>](../configuration-element.md)
- [<span data-ttu-id="6eb76-154">Risk azaltma: yeni 64-bit JıT derleyicisi</span><span class="sxs-lookup"><span data-stu-id="6eb76-154">Mitigation: New 64-bit JIT Compiler</span></span>](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
