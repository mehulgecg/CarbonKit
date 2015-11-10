![alt tag](https://github.com/ermalkaleci/CarbonTabSwipeNavigation/blob/master/carbonkit_logo.png)

CarbonKit is an OpenSource iOS library that includes powerful and beauty UI controllers. I started developing these controllers inspired by Android Material Design.

CarbonKit includes:
- CarbonSwipeRefresh
- CarbonTabSwipeNavigation

#Installation
CarbonKit is available on CocoaPods. Add to your Podfile:
```bash
pod 'CarbonKit'
```
and run 
```bash
pod install
```

# CarbonSwipeRefresh

![alt tag](https://github.com/ermalkaleci/CarbonTabSwipeNavigation/blob/master/Examples/CarbonSwipeRefresh.gif)

# SAMPLE CODE
```objective-c
#import "CarbonKit.h"

@interface ViewController ()
{
	CarbonSwipeRefresh *refresh;
}
@end

@implementation ViewController
- (void)viewDidLoad {
	[super viewDidLoad];

	refresh = [[CarbonSwipeRefresh alloc] initWithScrollView:self.tableView];
	[refresh setColors:@[
		[UIColor blueColor],
	 	[UIColor redColor],
		[UIColor orangeColor],
		[UIColor greenColor]]
	]; // default tintColor
	
	// If your ViewController extends to UIViewController
	// else see below
	[self.view addSubview:refresh];

	[refresh addTarget:self action:@selector(refresh:) forControlEvents:UIControlEventValueChanged];
}

- (void)refresh:(id)sender {
	[refresh endRefreshing];
}
@end
```

If you are using UITableViewController you must add the refreshControl into self.view.superview after viewDidApper
```objective-c
- (void)viewDidAppear:(BOOL)animated {
	[super viewDidAppear:animated];
	
	if (!refreshControl.superview) {
		[self.view.superview addSubview:refreshControl];
	}
}
```

# CarbonTabSwipeNavigation

![alt tag](https://github.com/ermalkaleci/CarbonTabSwipeNavigation/blob/CarbonKit_v2.x/Examples/CarbonTabSwipeNavigation.gif)

# SAMPLE CODE

```objective-c
#import "CarbonKit.h"

@interface ViewController () <CarbonTabSwipeDelegate>
@end

@implementation ViewController

- (void)viewDidLoad {
	[super viewDidLoad];

	NSArray *items = @[[UIImage imageNamed:@"home"], [UIImage imageNamed:@"hourglass"],
	[UIImage imageNamed:@"premium_badge"], @"Categories", @"Top Free",
	@"Top New Free", @"Top Paid", @"Top New Paid"];
	
	CarbonTabSwipeNavigation *carbonTabSwipeNavigation = 
	[[CarbonTabSwipeNavigation alloc] initWithItems:items rootViewController:self];
	
	[carbonTabSwipeNavigation setDelegate:self];
}

// delegate
- (UIViewController *)carbonTabSwipeNavigation:(CarbonTabSwipeNavigation *)carbontTabSwipeNavigation
			 viewControllerAtIndex:(NSUInteger)index {
	// return viewController at index
}

@end
```
# LICENSE
[The MIT License (MIT)](https://github.com/ermalkaleci/CarbonKit/blob/master/LICENSE)
