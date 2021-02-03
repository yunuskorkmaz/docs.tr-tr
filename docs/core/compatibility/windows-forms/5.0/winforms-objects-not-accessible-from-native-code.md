---
title: 'Son değişiklik: WinForms nesnelerine yerel koddan erişilemiyor'
description: Windows Forms nesnelerine artık yerel koddan erişemeyen .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 01/29/2021
ms.openlocfilehash: 53343f3f07817f735fa3b0ee77a352dcc80d4b6c
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506604"
---
# <a name="native-code-cant-access-windows-forms-objects"></a><span data-ttu-id="0cfd9-103">Yerel kod Windows Forms nesnelere erişemiyor</span><span class="sxs-lookup"><span data-stu-id="0cfd9-103">Native code can't access Windows Forms objects</span></span>

<span data-ttu-id="0cfd9-104">.NET 5,0 ' den başlayarak, artık Windows Forms nesneleri yerel koddan erişemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-104">Starting in .NET 5.0, you can no longer access Windows Forms objects from native code.</span></span>

## <a name="change-description"></a><span data-ttu-id="0cfd9-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0cfd9-105">Change description</span></span>

<span data-ttu-id="0cfd9-106">Önceki .NET sürümlerinde, bazı Windows Forms türler COM birlikte çalışabilirliğine görünür olarak tasarlanmıştı ve bu nedenle yerel kod tarafından erişilebilirdir.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-106">In previous .NET versions, some Windows Forms types were decorated as visible to COM interop, and thus were accessible to native code.</span></span> <span data-ttu-id="0cfd9-107">.NET 5,0 ' den başlayarak, COM birlikte çalışabilirliğine veya yerel koda erişilebilen Windows Forms API 'SI görünmez.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-107">Starting in .NET 5.0, no Windows Forms API are visible to COM interop or accessible to native code.</span></span> <span data-ttu-id="0cfd9-108">.NET çalışma zamanı artık kutudan çıkan özel tür kitaplıkları oluşturmayı desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-108">The .NET runtime no longer supports creating custom type libraries out of the box.</span></span> <span data-ttu-id="0cfd9-109">Ayrıca, .NET çalışma zamanı .NET Framework için tür kitaplığına bağlı olamaz (Bu, .NET Framework olduğu gibi sınıfların şeklinin sürdürülmesi gerekir).</span><span class="sxs-lookup"><span data-stu-id="0cfd9-109">In addition, the .NET runtime can't depend on the type library for .NET Framework (which would require maintaining the shape of classes as they were in .NET Framework).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0cfd9-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="0cfd9-110">Reason for change</span></span>

- <span data-ttu-id="0cfd9-111">`ComVisible(true)`Tür kitaplığı (tlb dosyası) oluşturma ve arama için kullanılan Numaralandırmalardan kaldırma: .NET Core tarafından sunulan bir WINFORMS tlb olmadığından, bu özniteliği tutma konusunda bir değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-111">Removal of `ComVisible(true)` from enumerations that were used for type library (TLB file) generation and lookup: Since there is no WinForms TLB provided by .NET Core, there's no value in keeping this attribute.</span></span>
- <span data-ttu-id="0cfd9-112">Sınıflardan kaldırma `ComVisible(true)` `AccessibleObject` : sınıflar CoCreateable değildir (parametresiz oluşturucusu yoktur) ve zaten var olan BIR örneği com 'a göstermek bu özniteliği gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-112">Removal of `ComVisible(true)` from `AccessibleObject` classes: The classes are not CoCreateable (they have no parameterless constructor), and exposing an already existing instance to COM does not require that attribute.</span></span>
- <span data-ttu-id="0cfd9-113">`ComVisible(true)` `Control` Ve `Component` sınıflarının kaldırılması: Bu, ÖRNEĞIN VB6 veya MFC gıbı WinForms denetimlerinin OLE/ActiveX aracılığıyla barındırılmasına izin vermek için kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-113">Removal of `ComVisible(true)` from `Control` and `Component` classes: This was used to allow hosting of WinForms controls via OLE/ActiveX, for example in VB6 or MFC.</span></span> <span data-ttu-id="0cfd9-114">Ancak, bu, artık sağlanmamış olan WinForms için bir TLB gerektirir ve ayrıca, aynı zamanda kutudan çıkar.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-114">However, this requires a TLB for WinForms, which is no longer provided, as well as registry-based activation, which also would not work out of the box.</span></span> <span data-ttu-id="0cfd9-115">Genellikle, WinForms denetimlerinin COM tabanlı barındırmasına yönelik bakım yoktu, bu nedenle destek, desteklenmeyen bir durumda bırakmak yerine kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-115">Generally, there was no maintenance of COM-based hosting of WinForms controls, so support was removed instead of leaving it in an unsupported state.</span></span>
- <span data-ttu-id="0cfd9-116">`ClassInterface`Denetimlerden özniteliklerin kaldırılması: OLE/ActiveX aracılığıyla barındırma desteklenmiyorsa, bu özniteliklerin artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-116">Removal of `ClassInterface` attributes from controls: If hosting via OLE/ActiveX is not supported, these attributes aren't needed anymore.</span></span> <span data-ttu-id="0cfd9-117">Bunlar, nesnelerin hala COM 'a açık olduğu ve özniteliğin ilgili olabileceği diğer yerlerde tutulur.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-117">They are kept in other places where objects are still exposed to COM and the attribute may be relevant.</span></span>
- <span data-ttu-id="0cfd9-118">' Nin `ComVisible(true)` kaldırılması `EventArgs` , büyük olasılıkla OLE/ActiveX barındırma ile kullanılmıştı ve artık desteklenmiyordur.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-118">Removal of `ComVisible(true)` from `EventArgs`: They were most likely used with OLE/ActiveX hosting, which is no longer supported.</span></span> <span data-ttu-id="0cfd9-119">Bunlar CoCreateable değildir, bu nedenle özniteliğin amacı yoktur.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-119">They are not CoCreateable either, so the attribute has no purpose.</span></span> <span data-ttu-id="0cfd9-120">Ayrıca, bir TLB sağlamaya gerek kalmadan mevcut örnekleri göstermek hiçbir fikir vermez.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-120">Also, exposing existing instances without providing a TLB makes no sense.</span></span>
- <span data-ttu-id="0cfd9-121">`ComVisible(true)`Temsilcilerden kaldırma: amaç bilinmiyor, ancak WinForms denetimlerinin ActiveX barındırılması artık desteklenmediğinden, herhangi bir kullanışsız olma olasılığı düşüktür.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-121">Removal of `ComVisible(true)` from delegates: Purpose is unknown, but since ActiveX hosting of WinForms Controls is no longer supported, it's unlikely to have any usefulness.</span></span>
- <span data-ttu-id="0cfd9-122">`ComVisible(true)`Genel olmayan bazı koddan kaldırma: tek potansiyel tüketici yeni Visual Studio Tasarımcısı olacaktır, ancak GUID belirtilmeden, yine de gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-122">Removal of `ComVisible(true)` from some non-public code: The only potential consumer would be the new Visual Studio designer, but without a GUID specified, it's unlikely that it's still needed.</span></span>
- <span data-ttu-id="0cfd9-123">`ComVisible(true)`Bazı rastgele Genel tasarımcı sınıflarından kaldırma: eski Visual Studio Tasarımcısı bu sınıflarla konuşmak IÇIN com birlikte çalışabilirliği kullanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-123">Removal of `ComVisible(true)` from some arbitrary public designer classes: The old Visual Studio designer may have been using COM interop to talk to these classes.</span></span> <span data-ttu-id="0cfd9-124">Ancak, eski tasarımcı .NET Core 'u desteklemez, bu nedenle çok sayıda kişi bu şekilde olmalıdır `ComVisible` .</span><span class="sxs-lookup"><span data-stu-id="0cfd9-124">However, the old designer doesn't support .NET Core, so few people would need these as `ComVisible`.</span></span>
- <span data-ttu-id="0cfd9-125">`IWin32Window` .NET Framework ' de tanımlanan aynı GUID ' de tanımlanmış, bu da tehlikeli sonuçlara sahip.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-125">`IWin32Window` defined the same GUID that was defined in .NET Framework, which has dangerous consequences.</span></span> <span data-ttu-id="0cfd9-126">.NET Framework birlikte çalışabilirliğine ihtiyacınız varsa kullanın `ComImport` .</span><span class="sxs-lookup"><span data-stu-id="0cfd9-126">If you require interop with .NET Framework, use `ComImport`.</span></span>
- <span data-ttu-id="0cfd9-127">Yönetilen WinForms `IDataObject` yapıldı `ComVisible` .</span><span class="sxs-lookup"><span data-stu-id="0cfd9-127">The WinForms managed `IDataObject` was made `ComVisible`.</span></span> <span data-ttu-id="0cfd9-128">Bu gerekli değildir, `ComImport` com birlikte çalışma için ayrı bir arabirim bildirimi vardır `IDataObject` .</span><span class="sxs-lookup"><span data-stu-id="0cfd9-128">This is not required, there is a separate `ComImport` interface declaration for `IDataObject` COM interop.</span></span> <span data-ttu-id="0cfd9-129">`IDataObject` `ComVisible` Hiçbir tlb sağlanmadığından ve sıralama her zaman başarısız olacağı için, yönetilmek için bir karşı üretken olma.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-129">It's counterproductive to have the managed `IDataObject` be `ComVisible`, since no TLB is provided and marshaling will always fail.</span></span> <span data-ttu-id="0cfd9-130">Ayrıca, GUID belirtilmemiş ve .NET Framework farklıydı, bu nedenle belgelenmemiş bir IID 'yi kaldırma işlemi müşterileri olumsuz etkileyecek.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-130">Also, the GUID was not specified and differed from .NET Framework, so its unlikely that removing an undocumented IID will affect customers negatively.</span></span>
- <span data-ttu-id="0cfd9-131">Kaldırma `ComVisible(false)` : Bunlar rastgele rastgele konumlara yerleştirilir ve varsayılan olarak SıNıFLARı com birlikte çalışabilirliğine sunmadığından gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-131">Removal of `ComVisible(false)`: Those are placed in seemingly arbitrary places and are redundant when the default is to not expose classes to COM interop.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0cfd9-132">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0cfd9-132">Version introduced</span></span>

<span data-ttu-id="0cfd9-133">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0cfd9-133">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0cfd9-134">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0cfd9-134">Recommended action</span></span>

<span data-ttu-id="0cfd9-135">Aşağıdaki örnek .NET Framework ve .NET Core 3,1 ' de çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-135">The following example works on .NET Framework and .NET Core 3.1.</span></span> <span data-ttu-id="0cfd9-136">Bu örnek, JavaScript 'In yansıma aracılığıyla form alt sınıfına geri çağırmasını sağlayan .NET Framework türü kitaplığına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-136">This example relies on the .NET Framework type library, which allows the JavaScript to call back into the form subclass via reflection.</span></span>

```cs
[PermissionSet(SecurityAction.Demand, Name="FullTrust")]
[System.Runtime.InteropServices.ComVisibleAttribute(true)]
public class Form1 : Form
{
    private WebBrowser webBrowser1 = new WebBrowser();

    protected override void OnLoad(EventArgs e)
    {
        webBrowser1.AllowWebBrowserDrop = false;
        webBrowser1.IsWebBrowserContextMenuEnabled = false;
        webBrowser1.WebBrowserShortcutsEnabled = false;
        webBrowser1.ObjectForScripting = this;

        webBrowser1.DocumentText =
            "<html><body><button " +
            "onclick=\"window.external.Test('called from script code')\">" +
            "call client code from script code</button>" +
            "</body></html>";
    }

    public void Test(String message)
    {
        MessageBox.Show(message, "client code");
    }
}
```

<span data-ttu-id="0cfd9-137">Örneğin, .NET 5,0 ve sonraki sürümlerde çalışmayı gerçekleştirmek için iki olası yol vardır:</span><span class="sxs-lookup"><span data-stu-id="0cfd9-137">There are two possible ways to make the example work on .NET 5.0 and later versions:</span></span>

- <span data-ttu-id="0cfd9-138">`ObjectForScripting`' I destekleyen Kullanıcı tarafından belirtilen bir nesne `IDispatch` (varsayılan olarak, proje düzeyinde değiştirilmedikleri takdirde, varsayılan olarak uygulanır) tanıtın.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-138">Introduce a user-declared `ObjectForScripting` object that supports `IDispatch` (which is applied by default, unless changed explicitly at the project level).</span></span>

  ```cs
  public class MyScriptObject
  {
      private Form1 _form;

      public MyScriptObject(Form1 form)
      {
          _form = form;
      }

      public void Test(string message)
      {
          MessageBox.Show(message, "client code");
      }
  }

  public partial class Form1 : Form
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = new MyScriptObject(this);

          ...
      }
  }
  ```

- <span data-ttu-id="0cfd9-139">Sergileme yöntemleriyle bir arabirim bildirin.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-139">Declare an interface with the methods to expose.</span></span>

  ```cs
  public interface IForm1
  {
      void Test(string message);
  }

  [ComDefaultInterface(typeof(IForm1))]
  public partial class Form1 : Form, IForm1
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = this;

          ...
      }
  }
  ```

## <a name="affected-apis"></a><span data-ttu-id="0cfd9-140">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0cfd9-140">Affected APIs</span></span>

<span data-ttu-id="0cfd9-141">Tüm Windows Forms API 'Leri.</span><span class="sxs-lookup"><span data-stu-id="0cfd9-141">All Windows Forms APIs.</span></span>

<!--

### Category

- Windows Forms

-->
