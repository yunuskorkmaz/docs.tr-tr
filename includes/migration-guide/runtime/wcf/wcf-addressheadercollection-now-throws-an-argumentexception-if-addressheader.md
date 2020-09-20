---
ms.openlocfilehash: e8b98e465228afd07432e737bb16aefb1b979973
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770890"
---
### <a name="wcf-addressheadercollection-now-throws-an-argumentexception-if-an-addressheader-element-is-null"></a><span data-ttu-id="40496-101">Bir addressHeader öğesi null ise, WCF AddressHeaderCollection şimdi bir ArgumentException oluşturur</span><span class="sxs-lookup"><span data-stu-id="40496-101">WCF AddressHeaderCollection now throws an ArgumentException if an addressHeader element is null</span></span>

#### <a name="details"></a><span data-ttu-id="40496-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="40496-102">Details</span></span>

<span data-ttu-id="40496-103">.NET Framework 4.7.1 ' den başlayarak, <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Oluşturucu <xref:System.ArgumentException> öğelerinden biri ise bir tane oluşturur `null` .</span><span class="sxs-lookup"><span data-stu-id="40496-103">Starting with the .NET Framework 4.7.1, the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.</span></span> <span data-ttu-id="40496-104">.NET Framework 4,7 ve önceki sürümlerde, hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="40496-104">In the .NET Framework 4.7 and earlier versions, no exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="40496-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="40496-105">Suggestion</span></span>

<span data-ttu-id="40496-106">Bu değişiklik ile .NET Framework 4.7.1 veya sonraki bir sürümde uyumluluk sorunlarıyla karşılaşırsanız, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek devre dışı bırakabilirsiniz `<runtime>` :</span><span class="sxs-lookup"><span data-stu-id="40496-106">If you encounter compatibility issues with this change on the .NET Framework 4.7.1 or a later version, you can opt-out of it by adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableAddressHeaderCollectionValidation=true" />
  </runtime>
</configuration>

| Name    | Value   |
|:--------|:--------|
| Scope   | Minor   |
| Version | 4.7.1   |
| Type    | Runtime |

#### Affected APIs

- <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>

<!--

#### Affected APIs

- `M:System.ServiceModel.Channels.AddressHeaderCollection.#ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})`

-->
